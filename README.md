# catchException

Esta es una clase de VFP que tiene como fin capturar las excepciones y grabarlas en un log y si es necesaria relanzarlas a nivel superior.

* support: raul.jrz@gmail.com
* url: [http://rauljrz.github.io/](http://rauljrz.github.io)


## Dependencies
**None! There is no dependency!**

## Installation
```
git clone https://github.com/raulvfp/catchException.git catchException
```

## Usage
**Properties:**
- **None! There are no defined properties**

**Methods:**
- init(bRelanzarThrow) : Es el unico metodo accesible. El metodo constructor.
	+ bRelanzarThrow: Booleano que indica si se relanza la excepcion con un THROW.

## Example:
1º - Este ejemplo no relanza la excepcion a nivel superior, sino que la controla en el bloque catch
```
    bRelanzarThrow = .F. &&NO Relanza la excepcion.
    TRY 
        *--- Este es una excepcion generada con THROW
        THROW lcExpectedValue 

    CATCH TO loEx
        loTmp = CREATEOBJECT('catchException', bRelanzarThrow)
        
        THIS.MessageOut('Esto me indica si es un error o algo generador por el programador: ' +loEx.Message)
        THIS.MessageOut('Valor de userValue: '+loEx.UserValue)
    ENDTRY

```

2º - Este ejemplo la execpcion es lanzada a un nivel superior para su control
```
    bRelanzarThrow = .T. &&Relanza la excepcion al nivel superior.
    TRY 
        *--- Este es una excepcion generada con THROW
        THROW lcExpectedValue 

    CATCH TO loEx
        loTmp = CREATEOBJECT('catchException', bRelanzarThrow)
        *-- No se ejecuta nada despues del CREATEOBJECT('catchException')
    ENDTRY

```
