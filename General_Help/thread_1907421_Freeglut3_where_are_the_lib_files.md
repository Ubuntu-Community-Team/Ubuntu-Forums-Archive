---
title: "Freeglut3: where are the lib files?"
date: 2012-01-11
forum: General Help
---

### Post by tomkat3 on 2012-01-11
Hello everybody,

I'm trying to use a program using OpenGL. I think the Makefile can find the freeglut OpenGL header files, but not the library files. Whatever I think, here are the errors it prints out when I tell it to make. Any help is appreciated!

```
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
| File JJVIEWER is generated.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++
gcc -o JJVIEWER object/array.o object/default.o object/display.o object/init.o object/keyboard.o object/main.o object/memory.o object/mouse.o object/read.o object/write.o -lm -L/usr/lib -L/usr/local/lib -lglut -lglu -lgl -ltiff
/usr/bin/ld: cannot find -lglu
/usr/bin/ld: cannot find -lgl
collect2: ld returned 1 exit status
make: *** [JJVIEWER] Error 1

```I think these are the problem lines in the Makefile:

```
CFLAGS          = -O -I$(INCPATH) -I$(SRCPATH) -I/usr/include -I/usr/include/GL -I/usr/local/include -DLINUX
LFLAGS          = -lm -L/usr/lib -L/usr/local/lib -lglut -lglu -lgl -ltiff

```

---

### Post by oldos2er on 2012-01-11
Closed, duplicate here: [http://ubuntuforums.org/showthread.php?t=1907561](http://ubuntuforums.org/showthread.php?t=1907561)

---

