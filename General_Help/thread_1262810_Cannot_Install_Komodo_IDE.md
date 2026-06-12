---
title: "Cannot Install Komodo IDE"
date: 2009-09-10
forum: General Help
---

### Post by roryneilsbutler on 2009-09-10
When I try running install.sh, I get this error in the terminal.

> ./INSTALLDIR/lib/python/bin/python2.4: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
root@rory-laptop:/home/rory/Desktop/Komodo-Professional-3.5.2-227956-linux-libcpp5-ix86# gedit install.sh
Even when running this as su, I still get this error.

Any form of help would be appreciated.

---

### Post by roryneilsbutler on 2009-09-10
I have python 2.5 installed, should I install 2.4?

---

### Post by roryneilsbutler on 2009-09-13
Anyone? Please? Sorry for the bump.

---

### Post by roryneilsbutler on 2009-09-15
I tried installing Python 2.4 but I get this error now:
> 
40055000-40079000 r-xp 00000000 08:01 1925141    /lib/tls/i686/cmov/libm-2.9.so
40079000-4007a000 r--p 00023000 08:01 1925141    /lib/tls/i686/cmov/libm-2.9.so
4007a000-4007b000 rw-p 00024000 08:01 1925141    /lib/tls/i686/cmov/libm-2.9.so
4007b000-401d7000 r-xp 00000000 08:01 1925137    /lib/tls/i686/cmov/libc-2.9.so
401d7000-401d8000 ---p 0015c000 08:01 1925137    /lib/tls/i686/cmov/libc-2.9.so
401d8000-401da000 r--p 0015c000 08:01 1925137    /lib/tls/i686/cmov/libc-2.9.so
401da000-401db000 rw-p 0015e000 08:01 1925137    /lib/tls/i686/cmov/libc-2.9.so
401db000-40261000 rw-p 401db000 00:00 0 
40261000-402a0000 r--p 00000000 08:01 5095449    /usr/lib/locale/en_US.utf8/LC_CTYPE
402b2000-402bf000 r-xp 00000000 08:01 1908798    /lib/libgcc_s.so.1
402bf000-402c0000 r--p 0000c000 08:01 1908798    /lib/libgcc_s.so.1
402c0000-402c1000 rw-p 0000d000 08:01 1908798    /lib/libgcc_s.so.1
bfe67000-bfe7c000 rw-p bffeb000 00:00 0          [stack]

make: *** [sharedmods] Error 134


Please, if anyone can lead me in the right direction.

---

### Post by roryneilsbutler on 2009-09-16
I finally fixed it by installing a missing lib file.

:guitar:

---

### Post by mihneasim on 2011-02-22
Can you tell us which lib was missing?
Thanks!

---

### Post by mihneasim on 2011-02-22
Nevermind, I fixed it this way:

make distclean
./configure BASECFLAGS=-U_FORTIFY_SOURCE
make

when compiling python (2.4 in my case)

---

