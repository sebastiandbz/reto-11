# reto-11

#### 1. Consulte que hacen los siguientes métodos de strings en python: endswith, startswith, isalpha, isalnum, isdigit, isspace, istitle, islower, isupper.

#### -endswith:   
######  Verifica si una cadena termina con un sufijo específico.

```python 
"archivo.txt".endswith(".txt")  # True
```

#### -startswith:   
######  Revisa si un texto empieza con algo.

```python 
"https://google.com".startswith("https")  # True
```

#### -isalpha:   
######  Dice si solo hay letras (sin números ni espacios).

```python 
"Hola".isalpha()     # True  
"Hola123".isalpha()  # False
```

#### -isalnum:   
######  Dice si hay letras y/o números, pero no símbolos ni espacios.

```python 
"Hola123".isalnum()  # True  
"Hola 123".isalnum() # False
```

#### -isdigit:   
######  Dice si el texto tiene solo números.

```python 
"2025".isdigit()  # True  
"20a5".isdigit()  # False
```

#### -isspace:   
######  Dice si hay solo espacios (o tabulaciones, saltos de línea).

```python 
"   ".isspace()  # True  
" a ".isspace()  # False
```

#### -istitle:   
######  Devuelve True si cada palabra de la cadena comienza con mayúscula y el resto en minúscula.

```python 
"Hola Mundo".istitle()  # True
"Hola mundo".istitle()  # False
```

#### -islower:   
######  Devuelve True si todos los caracteres alfabéticos están en minúscula.

```python 
"python".islower()  # True
"Python".islower()  # False
```

#### -isupper:   
######  Devuelve True si todos los caracteres alfabéticos están en mayúscula.

```python 
"PYTHON".isupper()  # True
"Python".isupper()  # False
```

#### 2 Procesar el archivo y extraer:

-Cantidad de vocales
 
-Cantidad de consonantes

-Listado de las 50 palabras que más se repiten

```python 
import requests
from collections import Counter
import string

# Descargar el archivo desde la URL
url = "https://www.py4e.com/code3/mbox.txt"
response = requests.get(url)
text = response.text

# Contadores
vocales = "aeiouAEIOU"
consonantes = "bcdfghjklmnpqrstvwxyzBCDFGHJKLMNPQRSTVWXYZ"
num_vocales = 0
num_consonantes = 0

# Conteo de palabras
palabras = []

# Procesar línea por línea
for linea in text.splitlines():
    # Contar letras
    for caracter in linea:
        if caracter in vocales:
            num_vocales += 1
        elif caracter in consonantes:
            num_consonantes += 1

    # Quitar puntuación y separar en palabras
    linea_limpia = linea.translate(str.maketrans('', '', string.punctuation))
    palabras.extend(linea_limpia.lower().split())

# Contar las palabras más comunes
conteo = Counter(palabras)
top_50 = conteo.most_common(50)

# Resultados
print(f"Cantidad de vocales: {num_vocales}")
print(f"Cantidad de consonantes: {num_consonantes}")
print("\nTop 50 palabras más comunes:")
for palabra, cantidad in top_50:
    print(f"{palabra}: {cantidad}")
```
