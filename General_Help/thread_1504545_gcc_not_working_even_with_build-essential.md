---
title: "gcc not working even with build-essential"
date: 2010-06-08
forum: General Help
---

### Post by fredster001 on 2010-06-08
Hi,

I've put the latest ubuntu (netbook version) on my netbook.
I installed g++ build-essential and gcc.

When I try to compile a .cpp file, it will work with g++ but not with gcc. It doesn't even work with a simple hello world....
The error message i get is:
```

$ gcc HelloWorld.cpp -o HelloWorld
/tmp/ccW2xrGx.o: In function `main':
HelloWorld.cpp:(.text+0x14): undefined reference to `std::cout'
HelloWorld.cpp:(.text+0x19): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/ccW2xrGx.o: In function `__static_initialization_and_destruction_0(int, int)':
HelloWorld.cpp:(.text+0x41): undefined reference to `std::ios_base::Init::Init()'
HelloWorld.cpp:(.text+0x46): undefined reference to `std::ios_base::Init::~Init()'
/tmp/ccW2xrGx.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


```



Any ideas please?
Thanks

---

### Post by Leppie on 2010-06-08
could you post the source code?

---

### Post by wmcbrine on 2010-06-08
It's not supposed to work with gcc... g++ = C++, gcc = C.

---

### Post by towheedm on 2010-06-08
> **wmcbrine said:**
> It's not supposed to work with gcc... g++ = C++, gcc = C.

Actually, the gcc user's manual says it can compile C++ code.

---

### Post by fredster001 on 2010-06-08
thanks guys - i've found the answer here
[http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html)

---

### Post by RiceMonster on 2010-06-08
> **towheedm said:**
> Actually, the gcc user's manual says it can compile C++ code.

It can, but you have to use the command g++ to compile it, rather than gcc.

---

