---
title: "Amule dowloaded from debian.org"
date: 2005-01-25
forum: General Help
---

### Post by ElChef on 2005-01-25
Hi, i have installed Ubuntu Linux warty, I installed via Synaptic  amule1.2.6+cvs20040620-1 but don't know why it closes randomly, then I download amule_1.2.6+rc7-1_i386.deb from debian.org that works very nice in my old Knoppix v3.6, when I try to install it at root console I get this:
# dpkg -i amule_1.2.6+rc7-1_i386.deb
(Leyendo la base de datos ...
68527 ficheros y directorios instalados actualmente.)
Preparando para reemplazar amule 1.2.6+rc7-1 (usando amule_1.2.6+rc7-1_i386.deb) ...
Leaving `diversion of /usr/bin/ed2k to /usr/bin/ed2k.xmule by amule'
Desempaquetando el reemplazo de amule ...
dpkg: problemas de dependencias impiden la configuración de amule:
 amule depende de libwxgtk2.4 (>= 2.4.2.6); sin embargo:
  Versión de libwxgtk2.4  en el sistema es 2.4.2.4ubuntu1.
dpkg: error al procesar amule (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 amule

I have installed: libwxbase2.4_2.4.2.6_i386.deb (downloaded agagin form debian) without any problem but I can't install amule rc7 ¿any idea to solve this?

---

