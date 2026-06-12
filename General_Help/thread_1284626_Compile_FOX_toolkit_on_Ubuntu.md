---
title: "Compile FOX toolkit on Ubuntu"
date: 2009-10-06
forum: General Help
---

### Post by tition on 2009-10-06
Dear all,

I just decided to switch to ubuntu. My main C++ project uses a widget toolkit called the FOX toolkit, [http://www.fox-toolkit.org/](http://www.fox-toolkit.org/)

I have not been able to go about compiling since I get the error message
../include/xincs.h:188:19: Fehler: X11/X.h: No such file or directory
../include/xincs.h:192:22: Fehler: X11/Xlib.h: No such file or directory
../include/xincs.h:196:22: Fehler: X11/Xcms.h: No such file or directory
../include/xincs.h:197:23: Fehler: X11/Xutil.h: No such file or directory
../include/xincs.h:198:27: Fehler: X11/Xresource.h: No such file or directory
../include/xincs.h:199:23: Fehler: X11/Xatom.h: No such file or directory
../include/xincs.h:200:28: Fehler: X11/cursorfont.h: No such file or directory

Trying to install 

sudo apt-get install xlibs-dev

(which appears to be recommended) I get the messages:

Paket xlibs-dev ist nicht verfügbar, wird aber von einem anderen
Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet
ist oder nur aus einer anderen Quelle verfügbar ist.

Translated,

The package xlibs-dev is not available, but is referenced by another package. That can mean that the package is missing or is available only from another source,

What should I do to fix the problem? 

I am absolute linux beginner. 

Thanks,
tition

---

