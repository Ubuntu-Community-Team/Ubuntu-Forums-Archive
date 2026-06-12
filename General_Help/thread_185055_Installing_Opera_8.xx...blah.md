---
title: "Installing Opera 8.xx...blah"
date: 2006-05-31
forum: General Help
---

### Post by master5o1 on 2006-05-31
How do I Install Opera 8.xxxxxxx (god know what numbers really...who cares.)

is there a wiki/thread that will help?

---

### Post by blackjack6.21.91 on 2006-05-31
are you running dapper drake or breezy badger??

---

### Post by master5o1 on 2006-05-31
<<<<<<<<<<< breezy

---

### Post by Sef on 2006-05-31
Here's a wiki:  [Install Opera.]("https://wiki.ubuntu.com/OperaBrowser?highlight=%28Opera%29")

---

### Post by lumpki on 2006-06-02
The easy way to install Opera (and other debs like Picasa for Linux):
1) open a terminal (gnome-terminal or konsole)
2) change to the directory containing the deb file, for example:
```
cd downloads
```
3) type this:
```
sudo dpkg -i opera-8.54-i386.deb
```

Done!

---

### Post by oskvaz on 2006-06-03
Problems: 

osk@ubuntu:~/Documents$ sudo dpkg -i opera_8.54-20060330.6-shared-qt_en_etch_i386.deb
Password:
Seleccionando el paquete opera previamente no seleccionado.
(Leyendo la base de datos ...
88203 ficheros y directorios instalados actualmente.)
Desempaquetando opera (de opera_8.54-20060330.6-shared-qt_en_etch_i386.deb) ...dpkg: problemas de dependencias impiden la configuración de opera: opera depende de xlib6g (>= 3.3.6) | xlibs; sin embargo:
  el paquete xlib6g no está instalado.
  el paquete xlibs no está instalado.
dpkg: error al procesar opera (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar: opera

Could anybody help me? ](*,)

---

