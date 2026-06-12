---
title: "no se como instalar un promgrama con la terminal"
date: 2009-08-05
forum: General Help
---

### Post by LuisMiguelCholoma on 2009-08-05
Hola soy nuevo en el foro y el mundo de ubuntu, y he aprendido un poco pero e querido instalar algunos programa y no tiene instaladores y la unica manera que he visto en otros foros es can la terminal pero no se como usarla ya que coloco los comando pero cuando voy a instalar nada no me los inatala, creo que debe ser por los archivoas los tengo en el escritorio pero si no funcionan desde el escritorio entonces donde debo meter los archivos, espero me ayuden ya que quiero instalar un reproductor de audio automatizado para una radio 

ha y otro favor, como descomprimo este archivo: rivendell-1.5.0-1.i586.rpm

Gracias espero no molestar mucho.

---

### Post by Xorlium on 2009-08-05
```

sudo su
apt-get update
apt-get install programa

```

Lo que tienes ahi es un .rpm, y ubuntu usa .deb. Entonces debes primero convertirlo en .deb con el programa "alien"

asi:

```

sudo su
apt-get update
apt-get install alien

```

Despues de instalarlo, te vas al directorio donde lo tienes y escribes
```

alien -d rivendell-1.5.0-1.i586.rpm 

```

Despues de eso hay que instalarlo. Para eso, debes escribir

```

dpkg -i rivendell*
apt-get install -f

```

Todo eso es como super-usuario (sudo su).

Espero te ayude.

---

### Post by LuisMiguelCholoma on 2009-08-09
todavía tengo problemas con la terminal hago lo que pusiste pero me tira u error 

E: dpkg se interrumpió, debe ejecutar manualmente sudo dpkg --configure  -a  para corregir el problema

---

### Post by LuisMiguelCholoma on 2009-08-09
Mi querido amigo  de ubuntu solo quiero hacerte una pregunta 
para poder instalar un programa en la terminal es necesario llevar los archivos a una carpeta que ya tiene como defecto ubuntu para que los comando de install los encuentre y los corra, pero mi inquietud es  como llego a esa carpeta en donde esta 

Espero me puedan ayudar
Gracias a los que me han estado respondiendo se los agradezco mucho

---

### Post by LuisMiguelCholoma on 2009-08-11
Hola soy nuevo en el mundo de ubuntu y en el foro, necesito de su ayuda 
No se pero me da un error por favor alguien me ayude ¿Que esoy haciendo mal?

luis@luis-desktop:~$ sudo aptitude install aMule-2.2.5
[sudo] password for luis: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "aMule-2.2.5"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "aMule-2.2.5"
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho

luis@luis-desktop:~$

---

