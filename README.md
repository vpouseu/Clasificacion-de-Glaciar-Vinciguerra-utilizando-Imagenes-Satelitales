# Clasificación de imágenes de satélite: Glaciar Vinciguerra
 
### Objetivo:
Generar una metodología para la cuantificación del área cubierta por nieve en la región de glaciar Vinciguerra, Tierra del Fuego, Argentina. Por medio de técnicas de teledetección (remote sensing) y de inteligencia artificial con el fin de determinar la evolución del glaciar en los últimos 5 años. ​​ 

***

## Introducción
<p align="justify">
El efecto del cambio climático global está teniendo un impacto significativo en los glaciares, los cuales desempeñan un papel crucial como reservorios de agua dulce. Los glaciares de la provincia de Tierra del Fuego, en la Patagonia Argentina, se encuentran entre los más afectados. El aumento de las temperaturas ha acelerado su retroceso y adelgazamiento a un ritmo sin precedentes en la historia y se estima que podrían ser los primeros en desaparecer de la cordillera de los Andes. Ante estos desafíos, es urgente tomar medidas para abordar el cambio climático y proteger los valiosos glaciares de la Patagonia resultando esencial realizar el monitoreo activo de los mismos que permita para predecir y mitigar los riesgos asociados.  
<p align="justify">
Actualmente, los glaciares se monitorean utilizando una combinación de técnicas como imágenes de satélite y mediciones en el terreno, que permiten obtener datos sobre la extensión, el espesor del hielo y el derretimiento. Sin embargo, a pesar de los esfuerzos realizados, se estima que solo alrededor del 1% de los glaciares se monitorea de manera continua y sistemática debido a las limitaciones logísticas y financieras. 
<p align="justify">
En este contexto, el uso de machine learning representa una oportunidad prometedora para abordar estas limitaciones ya que permiten el procesamiento automatizado y la interpretación de los grandes volúmenes de datos provistos por la teledetección. Estos algoritmos pueden aprender patrones y extraer características relevantes de las imágenes satelitales, lo que facilita la identificación de objetos, la detección de cambios. Esto agiliza y mejora la precisión del análisis de datos, lo que a su vez permite una monitorización más eficiente y detallada, proporcionando datos precisos y confiables. 
<p align="justify">
Con este trabajo, se busca, no solo analizar el retroceso del glaciar Vinciguerra, sino también proponer una metodología que ayude a evaluar la evolución de los glaciares a través del tiempo utilizando imágenes satelitales e inteligencia artificial, que respalde la conservación y la gestión sostenible de los recursos hídricos en la región de Tierra del Fuego. 
<p align="justify">
 

## Metodología propuesta
<p align="justify">
La detección, cálculo y evolución del área del glaciar Vinciguerra es un problema complejo que requiere un enfoque integral. A continuación, se describe un método propuesto que combina la adquisición de datos, el procesamiento de imágenes satelitales y técnicas de clasificación de machine learning.



<img src="https://docs.google.com/drawings/d/e/2PACX-1vSDbXC5kduo1AXAQubqFOEMG7uveGgCk_BfNZip_FfiebSue09RHiPpgU9Tcei5e_DHnTkFLklIwNST/pub?w=960&amp;h=720">



## Obtención de los datos
Adquisición de Datos 
<p align="justify">
En la presente sección, se aborda el e procedimiento empleado para obtener los datos necesarios para el desarrollo del proyecto. 

Selección de Imágenes: Sentinel-2B 
<p align="justify">
La selección de las imágenes Sentinel-2B como fuente primaria de datos se justifica por su capacidad para proporcionar información multiespectral y a su alta resolución espacial de 10 m.  Las imágenes Sentinel-2B, provenientes de la Agencia Espacial Europea (ESA), ofrecen bandas en el espectro visible e infrarrojo cercano, lo que permite discernir características específicas del terreno, como el hielo glaciar. La resolución temporal adecuada de estas imágenes facilita la monitorización de cambios estacionales y proporciona una visión integral de la evolución de los glaciares. 

### Selección temporal de imágenes para el proyecto. 

<p align="justify">
Se han seleccionado las imágenes correspondientes al período estival con un propósito crucial: durante esta época, los glaciares experimentan mayor deshielo y exposición, lo que resulta en una reducción de la cobertura de nieve y una mayor visibilidad de las características topográficas subyacentes. Esto permite una identificación y delimitación más precisa de los límites del glaciar, así como la detección de otros cuerpos de agua glacial como lagunas y lagos. 

### Plataforma de procesamiento  
<p align="justify">
Se utiliza la plataforma Google Earth Engine  para recolectar, procesar y descargar imágenes satelitales del área del glaciar. La utilización de esta herramienta posibilita el procesamiento de grandes volúmenes de datos de manera eficiente y su entorno de programación basado en JavaScript, permite automatizar y sistematizar los procesos de acceso y análisis. Otra de las ventajas es que la plataforma ofrece una biblioteca de funciones JavaScript que permiten a los usuarios realizar una amplia gama de tareas, como la visualización de imágenes, el procesamiento de datos y la generación de mapas 

### Selección de Area de Interes (AOI)
<p align="justify">
 ee.Geometry.Polygon( 

        [[[-68.34950104589618, -54.72003539154279], 

          [-68.34950104589618, -54.733814459689995], 

          [-68.32692757482684, -54.733814459689995], 

          [-68.32692757482684, -54.72003539154279]]
## Google Earth Engine:  Código de Procesamiento e Imágenes
<p align="justify">
Para obtener una representación coherente y de alta calidad del área de interés, se procede a la generación de un mosaico de imágenes. Este proceso implica aplicar filtros a la colección de imágenes Sentinel 2B seleccionada para eliminar nubes y sombras, y combinar las imágenes individuales para crear la imagen compuesta. 

https://code.earthengine.google.com/3b5a0312148a08abb1aee7145903e29b 


## Modelos de Clasificación Utilizados para el entrenamiento
### Modelos Supervisados
<p align="justify">

* K-Vecinos Más Cercanos (KNN): clasifica datos según la mayoría de vecinos cercanos en un espacio de características, siendo simple pero efectivo para clasificaciones locales. 

* Random Forest: es un conjunto de árboles de decisión que combina múltiples modelos para reducir el sobreajuste y mejorar la precisión en la clasificación.

* XGBoost: es un algoritmo de refuerzo que optimiza múltiples árboles de decisión secuencialmente, logrando altos niveles de precisión y eficiencia en la clasificación. 

* Máquinas de Soporte Vectorial (SVM): crea un hiperplano de separación óptimo para clasificar datos en categorías, siendo versátil y efectivo incluso en espacios de alta dimensionalidad. 

### AutoML:  TPOT 

<p align="justify">

En forma complementaria a los entrenamientos de los modelos propuestos se utiliza la herramienta de aprendizaje automático automatizado (AutoML) TPOT con el objetivo de encontrar las combinaciones óptimas de algoritmos predictivos y parámetros para solucionar el problema de clasificación propuesto. 

TPOT utiliza un enfoque de búsqueda de espacio de parámetros basado en algoritmos evolutivos para explorar diferentes combinaciones de algoritmos, hiperparámetros y características, y se puede utilizar para una amplia variedad de problemas de aprendizaje automático, incluyendo clasificación, regresión y clustering.
