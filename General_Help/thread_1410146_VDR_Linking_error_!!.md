---
title: "VDR Linking error !!"
date: 2010-02-18
forum: General Help
---

### Post by The Duke VIP on 2010-02-18
Hello everyone,

Don't know if this is the right section to ask such question :p
I'm writing a little test c++ program which make use of :
"/usr/include/vdr/thread.h"
"/usr/include/vdr/tools.h"
When compiling, I get the following Linker errors :

> Invoking: GCC C++ Linker
g++  -o"smartcard_PoC"  ./main_app.o   
./main_app.o: In function `main':
main_app.cpp: (.text+0xd37): undefined reference to `cMutex::cMutex()'
main_app.cpp: (.text+0xd6d): undefined reference to `cMutex::cMutex()'
main_app.cpp: (.text+0xdcd): undefined reference to `cMutex::Lock()'
main_app.cpp: (.text+0xddd): undefined reference to `cMutexLock::cMutexLock(cMutex*)'
main_app.cpp: (.text+0xdf4): undefined reference to `cMutexLock::~cMutexLock()'
main_app.cpp: (.text+0xdfc): undefined reference to `cMutex::Unlock()'
main_app.cpp: (.text+0xe6c): undefined reference to `strn0cpy(char*, char const*, unsigned int)'
main_app.cpp: (.text+0xe7d): undefined reference to `cMutexLock::~cMutexLock()'
main_app.cpp: (.text+0xea3): undefined reference to `cMutex::~cMutex()'

I've installed vdr package, but I didn't find any useful library to link against !!
Any help ?!

---

