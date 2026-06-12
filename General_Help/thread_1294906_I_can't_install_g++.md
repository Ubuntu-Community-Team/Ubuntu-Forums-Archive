---
title: "I can't install g++"
date: 2009-10-18
forum: General Help
---

### Post by AnGenesis on 2009-10-18
Hi, sorry by my english.

I can't install g++, when I try to install this appears:

stan@ubuntu:~$ sudo aptitude install g++
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
No se pudo encontrar ningún paquete que coincida con "g+". Sin embargo,
"g+" aparece en la descripción de los siguientes paquetes:
  libstdc++5 libstdc++6 
No se pudo encontrar ningún paquete que coincida con "g+". Sin embargo,
"g+" aparece en la descripción de los siguientes paquetes:
  libstdc++5 libstdc++6 
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho

I read about build essential but I receive this message:

sudo apt-get install build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
El paquete build-essential no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente
E: El paquete build-essential no tiene candidato para su instalación

---

### Post by jocampo on 2009-10-18
Try this

```

sudo aptitude update

```

```

sudo aptitude install build-essential 

```

Installing g++ is installing build essential. Once you finish you will be able to use the C++ compiler.

Baja o instala build-essential, es lo unico que necesitas para el compilador de C++

---

### Post by AnGenesis on 2009-10-19
Still not working.

sudo aptitude update
[sudo] password for stan: 
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages
Leyendo lista de paquetes... Hecho

sudo aptitude install build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
No se encontró ninguna versión candidata para build-essential
No se encontró ninguna versión candidata para build-essential
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho

=(

"Sigue sin funcionar"

---

### Post by OpenGuard on 2009-10-19
```
sudo aptitude show build-essential

```

Can you show us the output ?

---

### Post by AnGenesis on 2009-10-20
sudo aptitude show build-essential
[sudo] password for stan: 
No se encontró ninguna versión reciente o candidata para build-essential
Paquete: build-essential
Estado: no es un paquete real

---

### Post by OpenGuard on 2009-10-20
```
cat /etc/apt/sources.list

```

Let us know what you have there.

---

### Post by mc4man on 2009-10-20
Why don't you ck. that all the ubuntu software sources(repos) are enabled.

Don't know if this is in spanish on your install but anyway..

Go System -> Administration -> Software Sources and under the main tab (Ubuntu Software) make sure the first boxes are checked and  5th box is a solid color.

Under the Updates tab make sure the first 2 boxes are checked. (Important... and Recommended..
If you had to enable a repo then click close and reload

If still no good maybe try a different server (main page in Software Sources

You could also post this if continuing issues

```
cat /etc/apt/sources.list
```

---

### Post by AnGenesis on 2009-10-20
ohh, it works, thanks!!! :P

---

