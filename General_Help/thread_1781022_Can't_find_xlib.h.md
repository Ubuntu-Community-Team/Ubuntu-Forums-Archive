---
title: "Can't find xlib.h"
date: 2011-06-12
forum: General Help
---

### Post by dagoss on 2011-06-12
I'm trying to build a program called [Obpager]("http://obpager.sourceforge.net/"), but I'm getting an error saying I don't have xlib.h. From what I understand, that file is included in libx11-dev, which I have installed. Any idea?
```

dagoss@MAGIC-PORT:~/Downloads/obpager-1.8$ make
Compiling src/main.cc
In file included from src/main.cc:33:0:
src/OBPager.h:33:18: fatal error: Xlib.h: No such file or directory
compilation terminated.
cp: cannot stat `./objs/src/main.d': No such file or directory
/bin/sh: cannot open ./objs/src/main.d: No such file
Compiling src/OBPager.cc
In file included from src/OBPager.cc:20:0:
src/OBPager.h:33:18: fatal error: Xlib.h: No such file or directory
compilation terminated.
cp: cannot stat `./objs/src/OBPager.d': No such file or directory
/bin/sh: cannot open ./objs/src/OBPager.d: No such file
Linking obpager
g++: ./objs/src/main.o: No such file or directory
g++: ./objs/src/OBPager.o: No such file or directory
make: *** [obpager] Error 1
dagoss@MAGIC-PORT:~/Downloads/obpager-1.8$ sudo apt-get install libx11-dev
[sudo] password for dagoss: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libx11-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Yellow Pasque on 2011-06-12
The include statements needed tweaking. I attached the files I edited. Extract them to the obpager-1.8/src directory, overwriting the originals.

---

### Post by dagoss on 2011-06-13
Thank you so much! That was going to be my next step, but can't program my way out of a paper bag, so it would have taken me forever to figure that one out. Thanks a bunch.

---

