---
title: "Polyworld"
date: 2009-09-05
forum: General Help
---

### Post by Joesc on 2009-09-05
Hello everyone!

I am trying to set up polyworld on my (jaunty) ubuntu machine.

[http://www.beanblossom.in.us/larryy/polyworld.html](http://www.beanblossom.in.us/larryy/polyworld.html)

i have followed the instructions here: [http://www.beanblossom.in.us/larryy/BuildingPolyworld.html](http://www.beanblossom.in.us/larryy/BuildingPolyworld.html)

but when I go to the polyworld directory and run "make" it does not work.

it gives me a few error codes:            make[1]: *** [globals.o] Error 1
                                       then: make: [app] Error 2

---

### Post by NoaHall on 2009-09-05
Can you post the entire output? Thanks.

---

### Post by Joesc on 2009-09-05
---------------------------------
--- BUILDING: Polyworld Project
---------------------------------
</polyworld/.bld/app/Makefile: polyworld.pro>
mkdir -p /polyworld/.bld/app
mkdir -p /polyworld/.bld/PwMoviePlayer
mkdir -p /polyworld/.bld/CalcComplexity
mkdir -p /polyworld/.bld/pwtxt
mkdir -p /polyworld/bin
cd /polyworld/.bld/app/ && make --file Makefile
make[1]: Entering directory `/polyworld/.bld/app'
gcc -c -pipe -Wno-deprecated -fopenmp -g -D_GLIBCXX_DEBUG_PEDANTIC -Wno-deprecated -fopenmp -Wall -W -D_REENTRANT -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I/polyworld -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4 -I/polyworld -I../../agent -I../../app -I../../complexity -I../../environment -I../../graphics -I../../motion -I../../ui -I../../utils -I/usr/include/GL -I/usr/X11R6/include -I/polyworld -I/polyworld -I. -o globals.o /polyworld/app/globals.cp
In file included from /polyworld/app/globals.cp:9:
/polyworld/app/globals.h:15:20: error: qevent.h: No such file or directory
In file included from /polyworld/app/globals.cp:9:
/polyworld/app/globals.h:24: error: &#8216;QEvent&#8217; has not been declared
make[1]: *** [globals.o] Error 1
make[1]: Leaving directory `/polyworld/.bld/app'
make: *** [app] Error 2

---

### Post by NoaHall on 2009-09-05
I think you need to download qt 4.5

---

### Post by Joesc on 2009-09-05
I have QT creator 4.5.2

---

### Post by Joesc on 2009-09-05
[http://qt.nokia.com/downloads/downloads#lgpl](http://qt.nokia.com/downloads/downloads#lgpl)

this is the website i used to download it. and i got the lgpl/free linux 32 bit version

---

### Post by Catapults on 2009-10-02
I too have trouble setting up polyworld on 8.10. This is the result of *make.*

gcc -c -pipe -Wno-deprecated -g -D_GLIBCXX_DEBUG -D_GLIBCXX_DEBUG_PEDANTIC -Wno-deprecated -Wall -W -D_REENTRANT -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I../qtsdk-2009.04/qt/mkspecs/linux-g++ -I. -I../qtsdk-2009.04/qt/include/QtCore -I../qtsdk-2009.04/qt/include/QtGui -I../qtsdk-2009.04/qt/include -I. -Iapp -Icritter -Ienvironment -Igraphics -Iui -Iutils -I/include -I/include/QtOpenGL -I/include/QtCore -I/include/QtGui -I/usr/include/GL -I. -o debug.o app/debug.cp
In file included from app/debug.cp:9:
app/debug.h:29:8: warning: extra tokens at end of #endif directive
In file included from utils/error.h:11,
                 from graphics/gobject.h:23,
                 from graphics/gpolygon.h:8,
                 from environment/barrier.h:16,
                 from app/debug.cp:12:
app/debug.h:29:8: warning: extra tokens at end of #endif directive
In file included from app/debug.cp:13:
critter/critter.h:5:22: error: algobase.h: No such file or directory
In file included from app/debug.cp:12:
environment/barrier.h:59: error: extra qualification ‘barrier::’ on member ‘gXSortedBarriers’
make: *** [debug.o] Error 1

What do you make of this?

---

