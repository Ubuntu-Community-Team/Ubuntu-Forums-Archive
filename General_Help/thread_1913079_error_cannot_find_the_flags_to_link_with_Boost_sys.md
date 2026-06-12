---
title: "error: cannot find the flags to link with Boost system"
date: 2012-01-21
forum: General Help
---

### Post by grusty on 2012-01-21
I'm try to install Nightshade (Desktop planetarium) similar to Stellerium.

I have this error.

...
...
checking whether to build static libraries... yes
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for fabs in -lm... yes
checking for shm_open in -lrt... yes
checking for Boost headers version >= 1.42.0... yes
checking for Boost's header version... 1_46_1
checking for the toolset name used by Boost for g++... gcc46 -gcc
checking boost/system/error_code.hpp usability... yes
checking boost/system/error_code.hpp presence... yes
checking for boost/system/error_code.hpp... yes
checking for the Boost system library... no
configure: error: cannot find the flags to link with Boost system

I check, i have installed Boost libs. I can't find how solve it.

I have xubuntu 11.10. AMD processor, 2 gb ram. Nvidia Graphic

---

### Post by grusty on 2012-01-26
Any idea yet?

---

### Post by ronnycoolen on 2012-11-08
I just had this problem on another application that needs libboost. You need to install libboost-system-dev

---

