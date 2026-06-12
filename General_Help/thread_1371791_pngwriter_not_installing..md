---
title: "pngwriter not installing."
date: 2010-01-03
forum: General Help
---

### Post by FreezWay on 2010-01-03
I'm working on a program in c++ (fairly new to it) and I need to install pngwriter to use it, but i get this:
```
woot@woot-desktop:~/Desktop/pngwriter-0.5.4$ make
#
#
#  PNGwriter 0.5.4
#  Copyright 2002, 2003, 2004, 2005, 2006, 2007, 2008, 2009 Paul Blackburn
#  http://pngwriter.sourceforge.net/
#  This library and its associated files are covered
#  by the GNU General Public License.
#
#  Using make.include.linux for your compilation/installation prefs.
#
#  Important: If you do not have FreeType2 installed, 
#  see the README for instructions on compiling PNGwriter
#  without FreeType2 support.
#
#  Importante: Si no tienes FreeType2 instalado,
#  lee el archivo LEAME en doc/espaniol para 
#  instrucciones acerca de como compilar PNGwriter
#  sin soporte para FreeType2. 
#
#  You have selected to compile PNGwriter with
#  FreeType2 support.
#
#
cd src;	make 
make[1]: Entering directory `/home/woot/Desktop/pngwriter-0.5.4/src'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/woot/Desktop/pngwriter-0.5.4/src'
cd examples; make
make[1]: Entering directory `/home/woot/Desktop/pngwriter-0.5.4/examples'
g++ -O3 -Wall -Wno-deprecated `freetype-config --cflags` `freetype-config --libs` -I../src/ -I/usr/local/include/ pngtest.cc -o pngtest -L../src -L/usr/local/lib/ -lz -lpng -lpngwriter 
pngtest.cc:48:22: error: iostream.h: No such file or directory
make[1]: *** [pngtest] Error 1
make[1]: Leaving directory `/home/woot/Desktop/pngwriter-0.5.4/examples'
make: *** [examples] Error 2
woot@woot-desktop:~/Desktop/pngwriter-0.5.4$ 

```

---

### Post by happyhamster on 2010-01-03
- What you could try is: find the file pngtest.cc, in the folder /home/woot/Desktop/pngwriter-0.5.4/examples.

- Line 48 is probably: #include <iostream.h>

- Change that into: #include <iostream>

- Save, and recompile:

make clean

make

- Good luck.

---

