---
title: "Program compile error"
date: 2010-05-14
forum: General Help
---

### Post by UberDutch91 on 2010-05-14
Hi, 
I'm fairly new to linux and so far it's not been easy. I'm trying to install some software that i found at [http://sourceforge.net/projects/hantekdso/](http://sourceforge.net/projects/hantekdso/)

Here are the commands that i'm using:
```
./configure --without-arts --with-lib-preference="local system" -prefix=/usr
make
```It took me a while to get the ./configure to work but eventually it did configure correctly, i think. But now when I run make I continually get this error that nobody in the internet seems to have the answer to. Here is the output of the make command:

```
Makefile:864: warning: overriding commands for target `clean-bcheck'
Makefile:827: warning: ignoring old commands for target `clean-bcheck'
Makefile:869: warning: overriding commands for target `bcheck-am'
Makefile:832: warning: ignoring old commands for target `bcheck-am'
cd . && make -f admin/Makefile.common configure.in ;
make[1]: Entering directory `/home/breingan/Downloads/HantekDSO'
*** Creating configure.files
make[1]: Leaving directory `/home/breingan/Downloads/HantekDSO'
cd . && /bin/sh /home/breingan/Downloads/HantekDSO/admin/missing --run aclocal-1.10 
/home/breingan/Downloads/HantekDSO/admin/missing: line 52: aclocal-1.10: command not found
WARNING: `aclocal-1.10' is missing on your system.  You should only need it if
         you modified `acinclude.m4' or `configure.in'.  You might want
         to install the `Automake' and `Perl' packages.  Grab them from
         any GNU archive site.
 cd . && /bin/sh /home/breingan/Downloads/HantekDSO/admin/missing --run automake-1.10 --gnu 
/home/breingan/Downloads/HantekDSO/admin/missing: line 52: automake-1.10: command not found
WARNING: `automake-1.10' is missing on your system.  You should only need it if
         you modified `Makefile.am', `acinclude.m4' or `configure.in'.
         You might want to install the `Automake' and `Perl' packages.
         Grab them from any GNU archive site.
 cd . && perl admin/am_edit 
cd . && perl admin/am_edit Makefile.in
cd . && rm -f configure
cd . && make -f admin/Makefile.common configure
make[1]: Entering directory `/home/breingan/Downloads/HantekDSO'
configure.in:43: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:48: error: possibly undefined macro: AM_CONFIG_HEADER
configure.in:51: error: possibly undefined macro: AC_CHECK_COMPILERS
configure.in:52: error: possibly undefined macro: AC_ENABLE_SHARED
configure.in:53: error: possibly undefined macro: AC_ENABLE_STATIC
configure.in:58: error: possibly undefined macro: AM_KDE_WITH_NLS
configure.in:61: error: possibly undefined macro: AC_PATH_KDE
configure.in:70: error: possibly undefined macro: AC_CHECK_KDEMAXPATHLEN
make[1]: *** [configure] Error 1
make[1]: Leaving directory `/home/breingan/Downloads/HantekDSO'
make: *** [configure] Error 2

```I've googled for a solution, but none of them seem to work for me. If you have any thoughts please, let me know. I would greatly appreciate the help. Thanks.

---

### Post by gmargo on 2010-05-14
Install the **automake1.10** package (for 10.04 Lucid.)

---

### Post by UberDutch91 on 2010-05-14
Jeez... i'm an idiot. I had automake 1.9 instead of 1.10. It apparently doesn't work with that. Thank you for the response. It finally worked!

---

