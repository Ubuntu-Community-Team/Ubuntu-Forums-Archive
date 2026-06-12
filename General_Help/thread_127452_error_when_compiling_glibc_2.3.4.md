---
title: "error when compiling glibc 2.3.4"
date: 2006-02-08
forum: General Help
---

### Post by engineerdat on 2006-02-08
hi all,

am trying to compile glibc 2.3.4 on my breezy system.  im doing this to try to build an lfs system.  

anyway, i run 'sudo ../glibc-2.3.4/configure --prefix=/tools --disable-profile --enable-add-ons --enable-kernel=2.6.0 --with-binutils=/tools/bin --without-gd --with-headers=/tools/include --without-selinux'

from the glibc-build directory, then run 'sudo make' and get this error:

In file included from ../include/pthread.h:1,
                 from ../nptl/sysdeps/pthread/bits/libc-lock.h:23,
                 from ./gconv_int.h:25,
                 from gconv.c:23:
../nptl/sysdeps/pthread/pthread.h:664: error: array type has incomplete element type
make[2]: *** [/mnt/lfs/sources/glibc-build/iconv/gconv.o] Error 1
make[2]: Leaving directory `/mnt/lfs/sources/glibc-2.3.4/iconv'
make[1]: *** [iconv/subdir_lib] Error 2
make[1]: Leaving directory `/mnt/lfs/sources/glibc-2.3.4'
make: *** [all] Error 2

ps the instructions i'm following for installing glibc can be found here:  [http://www.linuxfromscratch.org/lfs/view/stable/chapter05/glibc.html](http://www.linuxfromscratch.org/lfs/view/stable/chapter05/glibc.html)

also, i found this page [http://www.mail-archive.com/pld-cvs-commit@pld-linux.org/msg00229.html](http://www.mail-archive.com/pld-cvs-commit@pld-linux.org/msg00229.html) that describes my problem, but i don't kknow what to do with it...

any ideas?  thx engineerdat

---

### Post by opioid on 2006-04-20
[http://www.linuxquestions.org/questions/showthread.php?p=2209426#post2209426](http://www.linuxquestions.org/questions/showthread.php?p=2209426#post2209426)

:)

---

