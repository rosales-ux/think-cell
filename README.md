# RV Chart Studio

Aplicación web para generar gráficas ejecutivas (cascada, columnas agrupadas, barras horizontales, líneas, columnas apiladas y dona) y conectar dos datos para mostrar su diferencia. Interfaz en español. Funciona sin servidor, claves API, instalación ni dependencias externas: es un solo `index.html`.

> Todos los datos de ejemplo son **ilustrativos** y no corresponden a una empresa real.

## 1. Crear el repositorio

1. Entre a [github.com](https://github.com) e inicie sesión.
2. Pulse **New repository**, escriba un nombre (por ejemplo `rv-chart-studio`) y elija **Public** (GitHub Pages gratuito requiere repositorio público, salvo planes de pago).
3. Pulse **Create repository**.

## 2. Subir el contenido del ZIP

1. Descomprima el ZIP en su equipo.
2. En el repositorio, pulse **Add file → Upload files**.
3. Arrastre **el contenido** de la carpeta descomprimida (no la carpeta): `index.html`, `README.md`, `.nojekyll`, `ejemplo-proyecto.json` y la carpeta `assets/`. `index.html` debe quedar en la raíz del repositorio.
4. Pulse **Commit changes**.

Si el navegador no deja subir `.nojekyll` (archivo oculto), no es obligatorio: la aplicación funciona igual.

## 3. Activar GitHub Pages

1. En el repositorio: **Settings → Pages**.
2. En **Build and deployment → Source** elija **Deploy from a branch**.
3. En **Branch** elija `main` y la carpeta `/(root)`. Pulse **Save**.
4. Espere uno o dos minutos. La dirección aparece en la misma pantalla: `https://SU-USUARIO.github.io/rv-chart-studio/`.

Todas las rutas son relativas, así que funciona tanto en esa dirección como abriendo `index.html` directamente desde su equipo.

## 4. Usar las gráficas y las conexiones

1. **Tipo de gráfica.** Escoja uno de los seis. Cambiar de tipo conserva datos y nombres de todas las series. La dona usa la primera serie y guarda las demás.
2. **Datos.** Edite la tabla (hasta 20 filas y 4 series) o péguela desde Excel con encabezados (tabulaciones o punto y coma; decimal con punto o coma; sin separador de miles). En cascada cada fila es **Total** (parte de cero) o **Cambio** (suma o resta al acumulado); los segmentos se aplican en el orden de las series y los totales se ingresan explícitamente. Con flecha arriba/abajo o Enter se mueve entre filas.
3. **Presentación.** Título, subtítulo, unidad, fuente, decimales (0, 1 o 2), valores y líneas guía. En *Colores, texturas y conectores*: 8 paletas, color por serie, restaurar colores, texturas (sólido, rayas, puntos, cuadrícula o combinación por serie) y color de conectores. Líneas y dona usan colores sólidos.
4. **Conectar datos.**
   - Pulse **Conectar datos**, seleccione el origen y luego el destino (con ratón, o con Tab y Enter/Espacio). **Cancelar selección** o Esc anulan el proceso.
   - Elija *Segmentos o puntos* para comparar el valor de la serie seleccionada, o *Totales* para comparar el total neto de la categoría (en cascada, el nivel acumulado). Puede cambiar de modo entre el origen y el destino.
   - Diferencia = destino − origen. Variación % = (destino − origen) / origen × 100. Si el origen es cero o negativo, el porcentaje muestra **N/D** y se conserva la diferencia.
   - *Comparaciones automáticas*: mes a mes, primero → último, y *Serie 2 → Serie 1* en cada categoría (el botón muestra los nombres reales).
   - *Elegir con listas desplegables*: origen y destino sin tocar la gráfica.
   - Cada conexión se puede editar (extremos, texto, formato de burbuja: valor, porcentaje o ambos), invertir, subir o bajar, eliminar; también **Eliminar todas** y **Deshacer**. Máximo 40; no se permiten duplicados (tampoco en sentido contrario: use *Invertir*). La dona no admite conexiones.
5. **Exportar.** SVG vectorial, PNG de alta resolución (3×, con el lienzo completo), proyecto JSON y HTML autónomo para trabajar sin conexión.

Las exportaciones SVG y PNG son imágenes: **no** son gráficas nativas de PowerPoint ni mantienen un vínculo con Excel. Para modificar una gráfica, vuelva a abrir el proyecto JSON.

## 5. Guardar y recuperar proyectos

- **Guardar proyecto (JSON)** descarga un archivo con datos, nombres, opciones visuales y conexiones.
- **Abrir proyecto JSON** lo restaura.
- La herramienta también guarda el último trabajo en el almacenamiento local del navegador. Eso **no se sincroniza entre dispositivos ni navegadores**, y se pierde si se borran los datos del sitio: descargue el JSON para conservar su trabajo.
- `ejemplo-proyecto.json` es un proyecto de muestra (Real, Presupuesto y Adicional, con colores y texturas).

## 6. Trasladar un proyecto desde otra versión

1. En la versión anterior, descargue el proyecto como JSON.
2. En esta versión, use **Abrir proyecto JSON**.
3. El archivo declara su versión (`version`). Los campos que falten se completan con valores por defecto; los que no se reconozcan se ignoran. Si el proyecto excede 20 categorías o 4 series, se conservan las primeras y se avisa. Las conexiones que apunten a datos inexistentes se descartan.
4. Revise el resultado y vuelva a guardar el JSON desde esta versión.

## Límites conocidos

- En columnas apiladas y cascadas con varias series, los segmentos de una misma columna pueden solaparse si los signos se mezclan (así lo implica aplicar los segmentos en orden).
- Con muchas conexiones el lienzo crece hacia arriba (o a la derecha en barras): use el desplazamiento horizontal o «Ajustar al ancho».
- Los textos del PNG usan la fuente Arial o equivalente del sistema donde se abra.
- No se probó en Safari ni Firefox; sí en Chromium (Chrome/Edge).
