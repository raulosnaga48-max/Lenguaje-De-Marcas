# UD0_ACT1

Nombre: Florian Raúl Osnaga Pavel
Curso: 1ASIR

## Ejercicio 1

Contenido del archivo textos.txt:

```
<h1>Texto grande</h1>
<h3>Texto pequeño</h3>
```

Primero lo abrí con el navegador siendo .txt y se ve el texto tal cual lo escribí, con las etiquetas y todo. Después lo cambié a textos.html y al abrirlo ya no salen las etiquetas. Sale "Texto grande" en letra grande y "Texto pequeño" más pequeño, los dos en negrita.

Conclusiones:

- El contenido es el mismo, solo he cambiado la extensión, así que el navegador decide cómo mostrar el archivo según la extensión.
- Si es .txt lo trata como texto normal y si es .html interpreta las etiquetas.
- Las etiquetas sirven para marcar qué es cada texto. La etiqueta h1 es un título grande y la h3 uno más pequeño, pero las etiquetas en sí no se ven.
- Un archivo html en realidad es un archivo de texto normal.

## Ejercicio 2

Archivo DAM.sgml:

```
<!DOCTYPE dam [
<!ELEMENT dam       - - (modulo+)>
<!ELEMENT modulo    - - (titulo, contenido)>
<!ELEMENT titulo    - - (#PCDATA)>
<!ELEMENT contenido - - (unidad+)>
<!ELEMENT unidad    - - (#PCDATA)>
]>
<dam>
  <modulo>
    <titulo>Lenguaje de Marcas</titulo>
    <contenido>
      <unidad>Introduccion</unidad>
      <unidad>HTML</unidad>
      <unidad>CSS</unidad>
    </contenido>
  </modulo>
  <modulo>
    <titulo>Programacion</titulo>
    <contenido>
      <unidad>Introduccion a la programacion</unidad>
      <unidad>Estructuras de control</unidad>
      <unidad>Funciones</unidad>
    </contenido>
  </modulo>
  <modulo>
    <titulo>Bases de Datos</titulo>
    <contenido>
      <unidad>Introduccion a las bases de datos</unidad>
      <unidad>Modelo relacional</unidad>
      <unidad>SQL</unidad>
    </contenido>
  </modulo>
</dam>
```

Vocabulario: dam, modulo, titulo, contenido, unidad

Reglas:

- dam tiene uno o varios modulo.
- Un modulo tiene un titulo y un contenido (en ese orden).
- contenido tiene una o varias unidad.
- Las unidad solo están dentro de contenido.
- titulo y unidad son solo texto.
- Después de una unidad solo puede ir otra unidad o el final de contenido.
- Después de un modulo solo puede ir otro modulo o el final de dam.

Las reglas las he escrito en la parte de arriba (el DOCTYPE). El "+" quiere decir "uno o más", y por eso se cumple lo de que detrás de una unidad solo va otra unidad o el fin de contenido.

## Ejercicio 3

Países del mundo.

Vocabulario: paises, pais, nombre, capital, continente, poblacion, idiomas, idioma. Además pais tiene un atributo "codigo".

Reglas:

- paises tiene uno o varios pais.
- Cada pais tiene nombre, capital, continente, poblacion e idiomas, en ese orden.
- Cada pais tiene que llevar el atributo "codigo".
- idiomas tiene uno o varios idioma.
- Lo demás es solo texto.

```
<!DOCTYPE paises [
<!ELEMENT paises     - - (pais+)>
<!ELEMENT pais       - - (nombre, capital, continente, poblacion, idiomas)>
<!ATTLIST pais       codigo CDATA #REQUIRED>
<!ELEMENT nombre     - - (#PCDATA)>
<!ELEMENT capital    - - (#PCDATA)>
<!ELEMENT continente - - (#PCDATA)>
<!ELEMENT poblacion  - - (#PCDATA)>
<!ELEMENT idiomas    - - (idioma+)>
<!ELEMENT idioma     - - (#PCDATA)>
]>
<paises>
  <pais codigo="ES">
    <nombre>Espana</nombre>
    <capital>Madrid</capital>
    <continente>Europa</continente>
    <poblacion>49000000</poblacion>
    <idiomas>
      <idioma>Castellano</idioma>
      <idioma>Catalan</idioma>
    </idiomas>
  </pais>
  <pais codigo="JP">
    <nombre>Japon</nombre>
    <capital>Tokio</capital>
    <continente>Asia</continente>
    <poblacion>124000000</poblacion>
    <idiomas>
      <idioma>Japones</idioma>
    </idiomas>
  </pais>
  <pais codigo="BR">
    <nombre>Brasil</nombre>
    <capital>Brasilia</capital>
    <continente>America</continente>
    <poblacion>212000000</poblacion>
    <idiomas>
      <idioma>Portugues</idioma>
    </idiomas>
  </pais>
</paises>
```

Los nombres no llevan tildes ni ñ para que no den problemas. La población es aproximada.

## Ejercicio 4

Para este he usado XML porque así puedo inventarme mis propias etiquetas (titulo, autor, isbn...).

Vocabulario: biblioteca, libro, titulo, autor, isbn, editorial, paginas, anio, idioma, sinopsis. El libro tiene un atributo "formato" que puede ser "papel" o "ebook".

Reglas:

- biblioteca tiene uno o varios libro.
- Cada libro tiene que tener el atributo "formato" con valor "papel" o "ebook".
- Dentro de libro van, en este orden: titulo, autor, isbn y editorial (obligatorios) y luego paginas, anio, idioma y sinopsis (opcionales, porque no todos los libros tienen esos datos).
- Todo es solo texto.

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE biblioteca [
<!ELEMENT biblioteca (libro+)>
<!ELEMENT libro (titulo, autor, isbn, editorial, paginas?, anio?, idioma?, sinopsis?)>
<!ATTLIST libro formato (papel | ebook) #REQUIRED>
<!ELEMENT titulo (#PCDATA)>
<!ELEMENT autor (#PCDATA)>
<!ELEMENT isbn (#PCDATA)>
<!ELEMENT editorial (#PCDATA)>
<!ELEMENT paginas (#PCDATA)>
<!ELEMENT anio (#PCDATA)>
<!ELEMENT idioma (#PCDATA)>
<!ELEMENT sinopsis (#PCDATA)>
]>
<biblioteca>
  <libro formato="papel">
    <titulo>Falco</titulo>
    <autor>Arturo Pérez-Reverte</autor>
    <isbn>9788420419688</isbn>
    <editorial>Alfaguara</editorial>
    <paginas>296</paginas>
    <idioma>Castellà</idioma>
  </libro>
  <libro formato="ebook">
    <titulo>Todo Alatriste</titulo>
    <autor>Arturo Pérez-Reverte</autor>
    <isbn>9788420425528</isbn>
    <editorial>Alfaguara</editorial>
    <idioma>Castellà</idioma>
  </libro>
  <libro formato="papel">
    <titulo>Hombres buenos</titulo>
    <autor>Arturo Pérez-Reverte</autor>
    <isbn>9788466329804</isbn>
    <editorial>Punto de Lectura</editorial>
    <anio>2024</anio>
    <sinopsis>La heróica aventura de quienes se atrevieron a cambiar el mundo con libros. En tiempos de oscuridad siempre hubo hombres buenos que lucharon para llevar las luces y el progreso. Y otros que procuraron impedirlo.</sinopsis>
  </libro>
</biblioteca>
```

Cosas que he decidido:

- Lo de "(En papel)" y "(EBOOK)" lo he puesto como atributo formato.
- En Falco el ISBN salía dos veces, lo he puesto solo una.
- Las mayúsculas del texto original las he quitado, porque eso es solo de cómo se ve y no del dato.
