---
title: "Problems with 32 bit and 64 bit libGL"
date: 2012-08-19
forum: General Help
---

### Post by javajames79 on 2012-08-19
I recently reinstalled ubuntu a new HDD as of problems i was having with my old drive. But i've been having trouble getting a lot of games running. Specifically games in windows - which are all 32 bit. The problem with all 32 bit games and is that for some reason, despite having 32 bit openGL installed they always report "wrong elf class" - i'm on a 64 bit system.

For example: when trying to run any game undr wine:

```
err:module:XYZdll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: wrong ELF class: ELFCLASS64
```When i try to run penumbra (which is only available under 32 bit:

```
./penumbra.bin: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS64
```This seems really odd to me; as if i check the /usr/lib32/libGL.so.1 it is a 32 bit file:

```
-------@------------:/usr/lib32$ file libGL.so.1
libGL.so.1: symbolic link to `/usr/lib32/libGL.so.1.2'
-------@------------:/usr/lib32$ file libGL.so.1.2
libGL.so.1.2: symbolic link to `/usr/lib32/fglrx/fglrx-libGL.so.1.2'
-------@------------:/usr/lib32$ file /usr/lib32/fglrx/fglrx-libGL.so.1.2
/usr/lib32/fglrx/fglrx-libGL.so.1.2: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
```I'm using the catalyst 12.6 driver for my AMD 6870, (from the AMD website rather than the additional driver tool - in my last installation, both worked exactly the same but i couldn't get the post release updates driver, for some errors, and the 12.6 driver was faster, so i haven't tried installing the driver from the additional driver tool after this install.)

The only thing i can think of is that it's attempting to use the 64 bit libraries. But if i do "linux32 ./overture" it does the exact same thing.

Any ideas? It's really bugging me that the install yielded different results.



Also, why can't i install the 64 bit and 32 bit versions of the runtime libraries (simultaneously)? I used to be able to do this and now i can't, and they shouldn't be conflicting because the 32 bit libraries should install to /usr/lib32 ????

---

### Post by javajames79 on 2012-08-19
Also, whenever i ldd a 32 bit executable that makes use of openGL i get "libGL.so.1 => not found"

---

### Post by javajames79 on 2012-08-19
Ok so near solution if i simply:

```
export LD_LIBRARY_PATH=/usr/lib32
```

Then i can run these 32 bit apps. But this is really annoying for me. (And i can imagine you can see why), is there anyway around this?

---

