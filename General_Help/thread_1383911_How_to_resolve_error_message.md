---
title: "How to resolve error message"
date: 2010-01-17
forum: General Help
---

### Post by dandeliondream on 2010-01-17
I'm trying to run a simple program in Ubuntu OS, Netbeans application but I cannot resolve the error message. Can someone please assist. Thank you.

/usr/bin/make -f nbproject/Makefile-Debug.mk SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/bee/NetBeansProjects/HelloWorld2'
/usr/bin/make  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/helloworld2
make[2]: Entering directory `/home/bee/NetBeansProjects/HelloWorld2'
mkdir -p build/Debug/GNU-Linux-x86
rm -f build/Debug/GNU-Linux-x86/main.o.d
gcc    -c -g -MMD -MP -MF build/Debug/GNU-Linux-x86/main.o.d -o build/Debug/GNU-Linux-x86/main.o main.cpp
mkdir -p dist/Debug/GNU-Linux-x86
gcc     -o dist/Debug/GNU-Linux-x86/helloworld2 build/Debug/GNU-Linux-x86/main.o  
build/Debug/GNU-Linux-x86/main.o: In function `__static_initialization_and_destruction_0':
/usr/include/c++/4.3/iostream:77: undefined reference to `std::ios_base::Init::Init()'
/usr/include/c++/4.3/iostream:77: undefined reference to `std::ios_base::Init::~Init()'
build/Debug/GNU-Linux-x86/main.o: In function `main':
/home/bee/NetBeansProjects/HelloWorld2/main.cpp:15: undefined reference to `std::cout'
/home/bee/NetBeansProjects/HelloWorld2/main.cpp:15: undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(int)'
build/Debug/GNU-Linux-x86/main.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/helloworld2] Error 1
make[2]: Leaving directory `/home/bee/NetBeansProjects/HelloWorld2'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/bee/NetBeansProjects/HelloWorld2'
make: *** [.build-impl] Error 2
BUILD FAILED (exit value 2, total time: 629ms)

```
#include <iostream>
#include <stdlib.h>

using namespace std;

int main() {

    cout << "Hello World" << endl;
    return (EXIT_SUCCESS);
}
```

---

### Post by lloyd_b on 2010-01-18
The problem appears to be that you're running "gcc", rather than "g++" to compile the code.  Since the code relies on C++ concepts (such as <iostream> and the 'std' namespace) you should really be using "g++" for compiling it.  Switch that, and the compile errors go away...

Lloyd B.

---

### Post by dandeliondream on 2010-01-18
> **lloyd_b said:**
> The problem appears to be that you're running "gcc", rather than "g++" to compile the code. Since the code relies on C++ concepts (such as <iostream> and the 'std' namespace) you should really be using "g++" for compiling it. Switch that, and the compile errors go away...
 
Lloyd B.
 
I'm a newbie to this. How do i know the issue is due to gcc compiler?

---

### Post by lloyd_b on 2010-01-19
> **dandeliondream said:**
> I'm a newbie to this. How do i know the issue is due to gcc compiler?

In this case, I knew there was a problem because you were using "include <iostream>", which should really never be used with standard C code - it's strictly C++.

Also, I've run across those oddball errors in the past in another thread, for pretty much the same reason.

Note that "g++" and "gcc" run the same actual compiler.  Invoking it as "g++" just sets some options that allows it to correctly compile C++ code, as opposed to standard C code.

Lloyd B.

---

### Post by dandeliondream on 2010-01-19
> **lloyd_b said:**
> In this case, I knew there was a problem because you were using "include <iostream>", which should really never be used with standard C code - it's strictly C++.
 
Also, I've run across those oddball errors in the past in another thread, for pretty much the same reason.
 
Note that "g++" and "gcc" run the same actual compiler. Invoking it as "g++" just sets some options that allows it to correctly compile C++ code, as opposed to standard C code.
 
Lloyd B.
 
Wow, this is an explicit explanation. I have learnt a great deal from you. Thanks for taking time to reply.

---

