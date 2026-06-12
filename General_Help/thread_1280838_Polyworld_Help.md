---
title: "Polyworld Help"
date: 2009-10-02
forum: General Help
---

### Post by Catapults on 2009-10-02
I need help setting Polyworld:oops:, I get this error when I do make in the terminal-


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



What do you think of this?

---

### Post by Catapults on 2009-10-12
hello?:-s

---

