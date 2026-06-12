---
title: "glibc 2.11 compile problem"
date: 2009-12-26
forum: General Help
---

### Post by weishigoname on 2009-12-26
I am using Ubuntu-9.10-amd64 version,my cpu is Intel double-core Cenlron T300+ ,In single usr mode ,I compile glibc2.11
commad: ../configure --prefix=/usr --with-headers=/usr/src/linux_x86_64/include --enable-add_ons
 
     make
and when I make ,problem occur
 ../nptl/sysdeps/pthread/pt-longjmp.c :29 error:'siglongjmp' aliased to undefined symbol 'longjmp'
The file in glibc-2.11/nptl/sysdeps/pthread directory,after error occured ,I checked that file ,and find a line #include"pthreadP.h"
but in that directory no that file exist.and I try make clean,and make again ,error is the same

---

### Post by SimaHWT on 2010-11-19
Sorry to bring this old thread up, but i got the same error and I didn't find how to fix yet. 

I'm using ubuntu 9.4 and I try to build glibc-2.12.1

---

