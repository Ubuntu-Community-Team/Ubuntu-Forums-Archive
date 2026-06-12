---
title: "Polyworld"
date: 2009-11-01
forum: General Help
---

### Post by Catapults on 2009-11-01
any idea what this means? I am trying to build polyworld, but it always quits with this error

```
:~/src/polyworld$ make
scons -f scripts/build/SConstruct
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o .bld/Polyworld/graphics/gstage.o -c -g -fopenmp -Isrc/environment -Isrc/motion -Isrc/agent -Isrc/graphics -Isrc/app -Isrc/complexity -Isrc/utils -Isrc/ui -Isrc/tools -Isrc/tools/genetrace -Isrc/tools/rancheck -Isrc/tools/PwMoviePlayer -Isrc/tools/pwtxt -Isrc/tools/CalcComplexity -Isrc/tools/PwMoviePlayer/English.lproj -I/usr/include/GL -I/usr/share/qt4/include -I/usr/share/qt4/include/QtCore -I/usr/share/qt4/include/QtGui -I/usr/share/qt4/include/QtOpenGL -I/usr/include src/graphics/gstage.cp
src/graphics/gstage.cp: In member function 'void gstage::SetLights(TGraphicsLightList*)':
src/graphics/gstage.cp:78: error: 'sprintf' was not declared in this scope
src/graphics/gstage.cp: In member function 'void gstage::AddLight(glight*)':
src/graphics/gstage.cp:266: error: 'sprintf' was not declared in this scope
scons: *** [.bld/Polyworld/graphics/gstage.o] Error 1
scons: building terminated because of errors.
make: *** [all] Error 2

```

please help:(

---

### Post by frikker on 2009-12-03
Hello.  Did you ever get this working? Here is what I had to do to get Polyworld working.

To fix your error, go into every file it complains about (in your case src/graphics/gstage.cp) and add the following to the top:
```
#include <stdio.h>
``` It will complain about l5 or 6 files.

After this is fixed, it will complain finally about a char * conversion error. Go into src/tools/pwtxt/main.cpp and on line 180 change
```
char *name = rindex( path, '/' );
```to
```
const char *name = rindex( path, '/' );
```

---

