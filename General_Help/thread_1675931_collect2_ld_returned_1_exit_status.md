---
title: "collect2: ld returned 1 exit status"
date: 2011-01-26
forum: General Help
---

### Post by wmaciel on 2011-01-26
Hey guys, I'm having a cruel problem here, I'm getting the following output when trying to compile my cpp project:

```
"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/walther/NetBeansProjects/CppPlay'
"/usr/bin/make"  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/cppplay
make[2]: Entering directory `/home/walther/NetBeansProjects/CppPlay'
mkdir -p dist/Debug/GNU-Linux-x86
g++     -lSDL -lSDLmain -lSDL_image -o dist/Debug/GNU-Linux-x86/cppplay build/Debug/GNU-Linux-x86/Sprite.o build/Debug/GNU-Linux-x86/Scene.o build/Debug/GNU-Linux-x86/Mouse.o build/Debug/GNU-Linux-x86/GameEngine.o build/Debug/GNU-Linux-x86/Keyboard.o build/Debug/GNU-Linux-x86/GameCanvas.o  
/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/crt1.o: In function `_start':
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/cppplay] Error 1
make[1]: *** [.build-conf] Error 2
make: *** [.build-impl] Error 2
make[2]: Leaving directory `/home/walther/NetBeansProjects/CppPlay'
make[1]: Leaving directory `/home/walther/NetBeansProjects/CppPlay'

BUILD FAILED (exit value 2, total time: 225ms)
```I've seen you guys replying to others about this collect2 error, but all of them had some kind of informative message from the compiler. My output, though, is not giving me any hint, do you have any idea what could this be? maybe point me in the right direction?

Thanks

---

### Post by wmaciel on 2011-01-26
I'm so embarrassed to say it guys, shortly after posting here I realized I didn't have a main function.
Sorry to bother. lol.

---

