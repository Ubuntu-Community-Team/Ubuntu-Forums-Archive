---
title: "Need help installing gcc 2.95 on ubuntu 11.04"
date: 2011-08-18
forum: General Help
---

### Post by Thorbenn on 2011-08-18
Hi,

i need help installing gnu gcc compiler 2.95 on ubuntu 11.04 32-bit system. I have no clue how i should install it. I need it though to compile a source code which was written for this specific version of gcc. I tried compiling it with the new gcc version 4.5 and it didn't work.


Thanks already ahead for your help ;)

---

### Post by dave01945 on 2011-08-18
have you already downloaded the source file if not you can get it here

[ftp://ftp.mirrorservice.org/sites/sourceware.org/pub/gcc/old-releases/gcc-2/](ftp://ftp.mirrorservice.org/sites/sourceware.org/pub/gcc/old-releases/gcc-2/)

and to install just type these commands in the directory you downloaded to

```
tar xvjf gcc-2.95.1.tar.bz2
cd gcc-2.95.1
./configure
make
sudo make install 
```

that should  do it 

hope it helps

---

### Post by Thorbenn on 2011-08-20
Hi when i give in make i get these tow errors at the end:

decl.c: In function ‘start_struct’:
decl.c:4449:27: error: argument ‘code’ doesn’t match prototype
ch-tree.h:736:13: error: prototype declaration
make[2]: *** [decl.o] Fehler 1
make[2]: Verlasse Verzeichnis '/home/tux/gcc/gcc/ch'
make[1]: *** [cc1chill] Fehler 2
make[1]: Verlasse Verzeichnis '/home/tux/gcc/gcc'
make: *** [all-gcc] Fehler 2

and again when i do sudo make install:

decl.c: In function ‘start_struct’:
decl.c:4449:27: error: argument ‘code’ doesn’t match prototype
ch-tree.h:736:13: error: prototype declaration
make[2]: *** [decl.o] Fehler 1
make[2]: Verlasse Verzeichnis '/home/tux/gcc/gcc/ch'
make[1]: *** [cc1chill] Fehler 2
make[1]: Verlasse Verzeichnis '/home/tux/gcc/gcc'
make: *** [install-gcc] Fehler 2

---

