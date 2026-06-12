---
title: "Karmic: Help!  qjoypad to control cursor-Errors attempting to 'make' &amp; 'make install'"
date: 2009-12-28
forum: General Help
---

### Post by m00nraker on 2009-12-28
HI!  I have been able to find help in previous threads about everything I've had any trouble with, but while installing qjoypad for use in games and to control the cursor using the following thread:
[http://ohioloco.ubuntuforums.org/showthread.php?t=1262470](http://ohioloco.ubuntuforums.org/showthread.php?t=1262470) 

When i got to the part in post #3 which states

 ./config     (worked fine)

make
sudo make install

i got the following errors:

donnie@donnie-laptop:~/qjoypad-4.0.0/src$ make
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DDEVDIR='\\\"/dev/input\\\"' -DICON24='\\\"/usr/local/share/pixmaps/qjoypad/icon24.png\\\"' -DICON64='\\\"/usr/local/share/pixmaps/qjoypad/icon64.png\\\"' -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -Itrayicon -I/usr/include/qt3 -o axis.o axis.cpp
<command-line>: warning: missing terminating " character
<command-line>: warning: missing terminating " character
<command-line>: warning: missing terminating " character
In file included from axis.cpp:1:
axis.h:7:18: error: QTimer: No such file or directory
axis.h:8:23: error: QTextStream: No such file or directory
axis.h:9:19: error: QRegExp: No such file or directory
axis.h:10:23: error: QStringList: No such file or directory
In file included from axis.cpp:1:
axis.h:21: error: expected class-name before ‘{’ token
axis.h:22: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
axis.h:24: error: expected ‘;’ before ‘friend’
axis.h:29: error: ‘QTextStream’ has not been declared
axis.h:31: error: ‘QTextStream’ has not been declared
axis.h:40: error: ‘QString’ does not name a type
axis.h:44: error: ‘QString’ does not name a type
axis.h:89: error: ISO C++ forbids declaration of ‘QTimer’ with no type
axis.h:89: error: expected ‘;’ before ‘*’ token
axis.h:90: error: expected ‘:’ before ‘slots’
axis.h:91: error: expected primary-expression before ‘void’
axis.h:91: error: ISO C++ forbids declaration of ‘slots’ with no type
axis.h:91: error: expected ‘;’ before ‘void’
axis.cpp: In constructor ‘Axis::Axis(int)’:
axis.cpp:15: error: ‘timer’ was not declared in this scope
axis.cpp:15: error: expected type-specifier before ‘QTimer’
axis.cpp:15: error: expected ‘;’ before ‘QTimer’
axis.cpp: In destructor ‘Axis::~Axis()’:
axis.cpp:24: error: ‘timer’ was not declared in this scope
axis.cpp: At global scope:
axis.cpp:27: error: ‘bool Axis::read’ is not a static member of ‘class Axis’
axis.cpp:27: error: ‘QTextStream’ was not declared in this scope
axis.cpp:27: error: ‘stream’ was not declared in this scope
axis.cpp:27: error: expected ‘,’ or ‘;’ before ‘{’ token
make: *** [axis.o] Error 1

If anyone is able to deduce what i have done wrong from this any help would be greatly appreciated!!!

It's not really that important i guess and i don't really play games...but i got a controller for krimmas and saw that it was possible to move the cursor with it so thought it would be neat...so no real dilemma or anything, still any help would be appreciated as i am developing an understanding of installation procedures.:smile:

---

### Post by airplus on 2009-12-29
Same here, anyone knows about this?

Thanks!

---

