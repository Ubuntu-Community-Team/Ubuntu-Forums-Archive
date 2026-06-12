---
title: "lib boost problem in 10.10 eclipse"
date: 2011-03-22
forum: General Help
---

### Post by andrissh on 2011-03-22
Hi folks,
I have:
installed eclipse on ubuntu 10.10
installed libbost 1.4 using sinaptic pkg manager
started a simple new c++ project,
#include <boost/thread.hpp>
int main(int argc, char* arg[]){
}
[COLOR=#000000][FONT=tahoma]I tried to build it, and had the error:[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"main.d"  -MT"main.d" -o"main.o" "../main.cpp"
In file included from /usr/include/boost/thread/detail/platform.hpp:17,
                 from /usr/include/boost/thread/thread.hpp:12,
                 from /usr/include/boost/thread.hpp:13,
                 from ../main.cpp:8:
/usr/include/boost/config/requires_threads.hpp:47:  error: #error "Compiler threading support is not turned on. Please set  the correct command line options for threading: -pthread (Linux), -pthreads (Solaris) or -mthreads (Mingw32)"
In file included from /usr/include/boost/thread/thread.hpp:12,
                 from  /usr/include/boost/thread.hpp:13,
                 from ../main.cpp:8:
/usr/include/boost/thread/detail/platform.hpp:67: error: #error "Sorry, no boost threads are available for this platform."
In file included from /usr/include/boost/thread.hpp:13,
                 from ../main.cpp:8:
/usr/include/boost/thread/thread.hpp:19: error: #error "Boost threads unavailable on this platform"[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]
[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]blablabla...so on... a lot more errors.[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]what am I missing here?[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]I dont understand the error message, and tried to write -pthread wherever I could, but did not work. 
[/FONT][/COLOR]
[COLOR=#000000][FONT=tahoma]Any tips? detailed or stepbystep solution please, because I am a beginner, and dont understand chinese:)[/FONT][/COLOR]
thank you guys

---

