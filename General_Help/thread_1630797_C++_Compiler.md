---
title: "C++ Compiler"
date: 2010-11-25
forum: General Help
---

### Post by WHYUMAD on 2010-11-25
Okay so I have to write a program from my computing class but the servers I usually use to compile my program on are down so therefore I have to grab it locally. 

I did grab and install "build-essentials". The compiler my class uses is "CC", that command doesnt work on my computer but "cc" does. Does anyone know what the difference is?

Before anyone suggests and other compiler, I HAVE TO use "CC". I can't use "gc++" (I believe thats the one I used in my previous class). I dont know why but thats what my prof wants. 

But anyway, "cc" works when I try to compile one file using 
"cc -c filename.cpp" but when I try to combine 2 files "cc -o filename1.o filename2.o" and make a runtime program I get a bunch of errors. This is what I am looking at so far:
```


User@lilbook:~/Documents/coding$ cc -o test1 main.o testfile1.o
main.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
testfile1.o: In function `testfile1::testfile1()':
testfile1.cpp:(.text+0x22): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator=(char const*)'
testfile1.o: In function `testfile1::testfile1()':
testfile1.cpp:(.text+0x7e): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator=(char const*)'
testfile1.o: In function `testfile1::testfile1(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, int, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
testfile1.cpp:(.text+0xd9): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator=(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
testfile1.o: In function `testfile1::testfile1(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, int, int, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)':
testfile1.cpp:(.text+0x149): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator=(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
testfile1.o: In function `testfile1::returnName()':
testfile1.cpp:(.text+0x1af): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
testfile1.o: In function `testfile1::operator=(testfile1)':
testfile1.cpp:(.text+0x203): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator=(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
testfile1.cpp:(.text+0x214): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
testfile1.cpp:(.text+0x22b): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
testfile1.o: In function `testfile1::operator<(testfile1)':
testfile1.cpp:(.text+0x288): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator=(char)'
testfile1.cpp:(.text+0x297): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::compare(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&) const'
testfile1.cpp:(.text+0x2a7): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
testfile1.cpp:(.text+0x2bc): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
testfile1.o: In function `testfile1::soft::soft()':
testfile1.cpp:(.text._ZN8testfile14softC1Ev[testfile1::soft::soft()]+0xf): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string()'
testfile1.cpp:(.text._ZN8testfile14softC1Ev[testfile1::soft::soft()]+0x2e): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
testfile1.o: In function `testfile1::soft::~soft()':
testfile1.cpp:(.text._ZN8testfile14softD1Ev[testfile1::soft::~soft()]+0x23): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
testfile1.cpp:(.text._ZN8testfile14softD1Ev[testfile1::soft::~soft()]+0x3a): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
testfile1.o: In function `std::list<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::_M_insert(std::_List_iterator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
testfile1.cpp:(.text._ZNSt4listISsSaISsEE9_M_insertESt14_List_iteratorISsERKSs[std::list<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::_M_insert(std::_List_iterator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x29): undefined reference to `std::_List_node_base::hook(std::_List_node_base*)'
testfile1.o: In function `__gnu_cxx::new_allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::destroy(std::basic_string<char, std::char_traits<char>, std::allocator<char> >*)':
testfile1.cpp:(.text._ZN9__gnu_cxx13new_allocatorISsE7destroyEPSs[__gnu_cxx::new_allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::destroy(std::basic_string<char, std::char_traits<char>, std::allocator<char> >*)]+0xd): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
testfile1.o: In function `std::list<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::_M_create_node(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
testfile1.cpp:(.text._ZNSt4listISsSaISsEE14_M_create_nodeERKSs[std::list<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::_M_create_node(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x60): undefined reference to `__cxa_begin_catch'
testfile1.cpp:(.text._ZNSt4listISsSaISsEE14_M_create_nodeERKSs[std::list<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::_M_create_node(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x77): undefined reference to `__cxa_rethrow'
testfile1.cpp:(.text._ZNSt4listISsSaISsEE14_M_create_nodeERKSs[std::list<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::_M_create_node(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x98): undefined reference to `__cxa_end_catch'
testfile1.o: In function `__gnu_cxx::new_allocator<std::_List_node<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::deallocate(std::_List_node<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >*, unsigned int)':
testfile1.cpp:(.text._ZN9__gnu_cxx13new_allocatorISt10_List_nodeISsEE10deallocateEPS2_j[__gnu_cxx::new_allocator<std::_List_node<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::deallocate(std::_List_node<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >*, unsigned int)]+0xd): undefined reference to `operator delete(void*)'
testfile1.o: In function `__gnu_cxx::new_allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::construct(std::basic_string<char, std::char_traits<char>, std::allocator<char> >*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
testfile1.cpp:(.text._ZN9__gnu_cxx13new_allocatorISsE9constructEPSsRKSs[__gnu_cxx::new_allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::construct(std::basic_string<char, std::char_traits<char>, std::allocator<char> >*, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)]+0x31): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
testfile1.o: In function `__gnu_cxx::new_allocator<std::_List_node<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::allocate(unsigned int, void const*)':
testfile1.cpp:(.text._ZN9__gnu_cxx13new_allocatorISt10_List_nodeISsEE8allocateEjPKv[__gnu_cxx::new_allocator<std::_List_node<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::allocate(unsigned int, void const*)]+0x24): undefined reference to `std::__throw_bad_alloc()'
testfile1.cpp:(.text._ZN9__gnu_cxx13new_allocatorISt10_List_nodeISsEE8allocateEjPKv[__gnu_cxx::new_allocator<std::_List_node<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >::allocate(unsigned int, void const*)]+0x38): undefined reference to `operator new(unsigned int)'
testfile1.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
testfile1.o:(.eh_frame+0x83): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```


I assume either im using the wrong compiler or my settings are wrong.

Thanks for the help!

---

### Post by sgosnell on 2010-11-25
Linux is case-sensitive, so CC is not the same as cc, nor cC, nor Cc.  They're all different.  Linux programs are always lower-case, all the way.

The error messages you're getting indicate that you don't have proper code in testfile.o.  You're using the correct compiler, but you have to fix your code.

---

### Post by WHYUMAD on 2010-11-25
Ugh... I really really dont wanna post my code somewhere since it is a project and its just basic code. I guess ill make a test file that basically couts something and see if it still does it. The only other time I got errors like that is when it was the wrong compiler, otherwise I usually have an error that says the line number and whats wrong. Which happens when I use "cc -c" but not "cc - o"

also it creates a file called "filename.h.gch" .. I have never seen a gch extension before ever when using "cc"

---

### Post by Gunman1982 on 2010-11-25
Well there is nothing wrong with your code but you are missing some includes, try
'gcc -lstdc++ <source> ' (or cc instead of gcc but I guess its the same anyway)

You are trying to compile c++ code here and gcc expects that you want to compile c code so it doesn't include the c++ related stuff by default.

---

### Post by James78 on 2010-11-25
Why not just use g++?

---

### Post by Simian Man on 2010-11-25
cc is just a symbolic link to gcc.  It's the same compiler.  It's clear from your error messages that you are writing C++ code and not C code.  You should really use the "g++" command to compile your code.

---

