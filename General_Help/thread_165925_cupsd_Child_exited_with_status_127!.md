---
title: "cupsd: Child exited with status 127!"
date: 2006-04-25
forum: General Help
---

### Post by rkruse on 2006-04-25
I tried to update cups, but I did something wrong and it stopped working.
I have uninstalled and installed cupsys and related packages with apt-get, aptitude and synaptic but I can't get cupsys to operate. For instance,

unsinstall:

sudo apt-get remove --purge cupsys

and install back:

rkruse@calisto:~$ sudo apt-get install cupsys
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Paquetes sugeridos:
  cupsys-bsd cupsys-driver-gimpprint foomatic-bin foomatic-filters-ppds
  xpdf-korean xpdf-japanese xpdf-chinese-traditional xpdf-chinese-simplified
  cups-pdf hplip
Se instalarán los siguientes paquetes NUEVOS:
  cupsys
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0B/8963kB de archivos.
Se utilizarán 16.3MB de espacio de disco adicional después de desempaquetar.

Preconfigurando paquetes ...
Seleccionando el paquete cupsys previamente no seleccionado.
(Leyendo la base de datos ...
138334 ficheros y directorios instalados actualmente.)
Desempaquetando cupsys (de .../cupsys_1.1.23-10ubuntu4_i386.deb) ...
Configurando cupsys (1.1.23-10ubuntu4) ...
Starting Common Unix Printing System: cupsd                              [ ok ]

But:

rkruse@calisto:~$ ps -e | grep cups
rkruse@calisto:~$

Or:

rkruse@calisto:~$ sudo /usr/sbin/cupsd
cupsd: Child exited with status 127!

Without success.
Any ideas?

---

