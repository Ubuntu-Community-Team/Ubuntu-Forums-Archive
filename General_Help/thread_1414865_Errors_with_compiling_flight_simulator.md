---
title: "Errors with compiling flight simulator"
date: 2010-02-24
forum: General Help
---

### Post by ..::| Dave89 |::.. on 2010-02-24
I came across a flight simulator called Aviation on a magazine cover DVD, and attempting to compile it, I get this error: 

dave89@dave89-laptop:~$ cd /home/dave89/Downloads/columbia-0.1
dave89@dave89-laptop:~/Downloads/columbia-0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for luac5.1... no
checking for luac51... no
checking for luac... no
./configure: line 2213: -v: command not found
configure: error: 
Lua 5.1 was found but the default Lua compiler does not seem to
be version 5.1.  You have to manually set the variable LUAC to the
path to the Lua 5.1 compiler.
      
dave89@dave89-laptop:~/Downloads/columbia-0.1$ 

I don't know what this means, I have very little experience compiling apps from source, if anyone can tell me what this means, and how to fix it, I'd be very happy.  TIA

Website for flight sim is: [http://www.nongnu.org/aviation/](http://www.nongnu.org/aviation/)

---

### Post by darolu on 2010-02-24
You need to meet all your dependencies first.

```
checking for gawk... **no**
checking for luac5.1... **no**
checking for luac51... **no**
checking for luac... **no**
```

You'll have to install those packages first.

Try to find a .deb file of the game, it's easier, sometimes I find good ones at: [http://www.playdeb.net](http://www.playdeb.net)

---

### Post by ..::| Dave89 |::.. on 2010-02-24
I couldn't find any .deb file of the game on that site, I'll do a Google search in a minute. 

Unfortunately, installing the dependencies require the Ubuntu CD for installation.  I didn't pack the CD before leaving for our vacation, but I have the Ubuntu ISO on my external HD here, I'll have to get a blank CD tomorrow, before I can continue :(

---

### Post by 3rdalbum on 2010-02-24
> **..::| Dave89 |::.. said:**
> I couldn't find any .deb file of the game on that site, I'll do a Google search in a minute. 

Unfortunately, installing the dependencies require the Ubuntu CD for installation.  I didn't pack the CD before leaving for our vacation, but I have the Ubuntu ISO on my external HD here, I'll have to get a blank CD tomorrow, before I can continue :(

No, just uncheck the CD in System > Administration > Software Sources and it will get the packages from the internet instead.

---

### Post by ..::| Dave89 |::.. on 2010-02-24
I installed luac and gawk, now asks me to install techne from [http://savannah.nongnu.org/projects/techne/](http://savannah.nongnu.org/projects/techne/)
 
 but attempting to compile this I get:
 
 ```
dave89@dave89-laptop:~/Downloads/columbia-0.1$ cd  /home/dave89/Downloads/techne-0.1
 dave89@dave89-laptop:~/Downloads/techne-0.1$ ./configure
 checking for a BSD-compatible install... /usr/bin/install -c
 checking whether build environment is sane... yes
 checking for a thread-safe mkdir -p... /bin/mkdir -p
 checking for gawk... gawk
 checking whether make sets $(MAKE)... yes
 checking for style of include used by make... GNU
 checking for gcc... gcc
 checking for C compiler default output file name... a.out
 checking whether the C compiler works... yes
 checking whether we are cross compiling... no
 checking for suffix of executables... 
 checking for suffix of object files... o
 checking whether we are using the GNU C compiler... yes
 checking whether gcc accepts -g... yes
 checking for gcc option to accept ISO C89... none needed
 checking dependency style of gcc... gcc3
 checking how to run the C preprocessor... gcc -E
 checking for grep that handles long lines and -e... /bin/grep
 checking for egrep... /bin/grep -E
 checking for ANSI C header files... yes
 checking for sys/types.h... yes
 checking for sys/stat.h... yes
 checking for stdlib.h... yes
 checking for string.h... yes
 checking for memory.h... yes
 checking for strings.h... yes
 checking for inttypes.h... yes
 checking for stdint.h... yes
 checking for unistd.h... yes
 checking minix/config.h usability... no
 checking minix/config.h presence... no
 checking for minix/config.h... no
 checking whether it is safe to define __EXTENSIONS__... yes
 checking for gcc... (cached) gcc
 checking whether we are using the GNU C compiler... (cached) yes
 checking whether gcc accepts -g... (cached) yes
 checking for gcc option to accept ISO C89... (cached) none needed
 checking dependency style of gcc... (cached) gcc3
 checking whether gcc and cc understand -c and -o together... yes
 checking for gcc... gcc
 checking whether we are using the GNU Objective C compiler... no
 checking whether gcc accepts -g... no
 checking dependency style of gcc... gcc3
 checking how to run the Objective C preprocessor... /lib/cpp
 configure: error: in `/home/dave89/Downloads/techne-0.1':
 configure: error: Objective C preprocessor "/lib/cpp" fails sanity check
 See `config.log' for more details.
```
 
 Here is the contents of "config.log"
 
 ```
This file contains any messages produced by compilers while
 running configure, to aid debugging if configure makes a mistake.
 
 It was created by techne configure 0.1, which was
 generated by GNU Autoconf 2.64.  Invocation command line was
 
   $ ./configure 
 
 ## --------- ##
 ## Platform. ##
 ## --------- ##
 
 hostname = dave89-laptop
 uname -m = i686
 uname -r = 2.6.31-19-generic
 uname -s = Linux
 uname -v = #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010
 
 /usr/bin/uname -p = unknown
 /bin/uname -X     = unknown
 
 /bin/arch              = unknown
 /usr/bin/arch -k       = unknown
 /usr/convex/getsysinfo = unknown
 /usr/bin/hostinfo      = unknown
 /bin/machine           = unknown
 /usr/bin/oslevel       = unknown
 /bin/universe          = unknown
 
 PATH: /usr/local/sbin
 PATH: /usr/local/bin
 PATH: /usr/sbin
 PATH: /usr/bin
 PATH: /sbin
 PATH: /bin
 PATH: /usr/games
 
 
 ## ----------- ##
 ## Core tests. ##
 ## ----------- ##
 
 configure:2351: checking for a BSD-compatible install
 configure:2419: result: /usr/bin/install -c
 configure:2430: checking whether build environment is sane
 configure:2480: result: yes
 configure:2621: checking for a thread-safe mkdir -p
 configure:2660: result: /bin/mkdir -p
 configure:2673: checking for gawk
 configure:2689: found /usr/bin/gawk
 configure:2700: result: gawk
 configure:2711: checking whether make sets $(MAKE)
 configure:2733: result: yes
 configure:2828: checking for style of include used by make
 configure:2856: result: GNU
 configure:2926: checking for gcc
 configure:2942: found /usr/bin/gcc
 configure:2953: result: gcc
 configure:3182: checking for C compiler version
 configure:3191: gcc --version >&5
 gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1
 Copyright (C) 2009 Free Software Foundation, Inc.
 This is free software; see the source for copying conditions.  There is  NO
 warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR  PURPOSE.
 
 configure:3202: $? = 0
 configure:3191: gcc -v >&5
 Using built-in specs.
 Target: i486-linux-gnu
 Configured with: ../src/configure -v --with-pkgversion='Ubuntu  4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs  --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr  --enable-shared --enable-multiarch --enable-linker-build-id  --with-system-zlib --libexecdir=/usr/lib --without-included-gettext  --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4  --program-suffix=-4.4 --enable-nls --enable-clocale=gnu  --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all  --disable-werror --with-arch-32=i486 --with-tune=generic  --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu  --target=i486-linux-gnu
 Thread model: posix
 gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 
 configure:3202: $? = 0
 configure:3191: gcc -V >&5
 gcc: '-V' option must have argument
 configure:3202: $? = 1
 configure:3191: gcc -qversion >&5
 gcc: unrecognized option '-qversion'
 gcc: no input files
 configure:3202: $? = 1
 configure:3224: checking for C compiler default output file name
 configure:3246: gcc    conftest.c  >&5
 configure:3250: $? = 0
 configure:3287: result: a.out
 configure:3303: checking whether the C compiler works
 configure:3312: ./a.out
 configure:3316: $? = 0
 configure:3331: result: yes
 configure:3338: checking whether we are cross compiling
 configure:3340: result: no
 configure:3343: checking for suffix of executables
 configure:3350: gcc -o conftest    conftest.c  >&5
 configure:3354: $? = 0
 configure:3376: result: 
 configure:3382: checking for suffix of object files
 configure:3404: gcc -c   conftest.c >&5
 configure:3408: $? = 0
 configure:3429: result: o
 configure:3433: checking whether we are using the GNU C compiler
 configure:3452: gcc -c   conftest.c >&5
 configure:3452: $? = 0
 configure:3461: result: yes
 configure:3470: checking whether gcc accepts -g
 configure:3490: gcc -c -g  conftest.c >&5
 configure:3490: $? = 0
 configure:3531: result: yes
 configure:3548: checking for gcc option to accept ISO C89
 configure:3612: gcc  -c -g -O2  conftest.c >&5
 configure:3612: $? = 0
 configure:3625: result: none needed
 configure:3647: checking dependency style of gcc
 configure:3757: result: gcc3
 configure:3778: checking how to run the C preprocessor
 configure:3809: gcc -E  conftest.c
 configure:3809: $? = 0
 configure:3823: gcc -E  conftest.c
 conftest.c:11:28: error: ac_nonexistent.h: No such file or directory
 configure:3823: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | /* end confdefs.h.  */
 | #include <ac_nonexistent.h>
 configure:3848: result: gcc -E
 configure:3868: gcc -E  conftest.c
 configure:3868: $? = 0
 configure:3882: gcc -E  conftest.c
 conftest.c:11:28: error: ac_nonexistent.h: No such file or directory
 configure:3882: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | /* end confdefs.h.  */
 | #include <ac_nonexistent.h>
 configure:3911: checking for grep that handles long lines and -e
 configure:3969: result: /bin/grep
 configure:3974: checking for egrep
 configure:4036: result: /bin/grep -E
 configure:4041: checking for ANSI C header files
 configure:4061: gcc -c -g -O2  conftest.c >&5
 configure:4061: $? = 0
 configure:4134: gcc -o conftest -g -O2   conftest.c  >&5
 configure:4134: $? = 0
 configure:4134: ./conftest
 configure:4134: $? = 0
 configure:4145: result: yes
 configure:4158: checking for sys/types.h
 configure:4158: gcc -c -g -O2  conftest.c >&5
 configure:4158: $? = 0
 configure:4158: result: yes
 configure:4158: checking for sys/stat.h
 configure:4158: gcc -c -g -O2  conftest.c >&5
 configure:4158: $? = 0
 configure:4158: result: yes
 configure:4158: checking for stdlib.h
 configure:4158: gcc -c -g -O2  conftest.c >&5
 configure:4158: $? = 0
 configure:4158: result: yes
 configure:4158: checking for string.h
 configure:4158: gcc -c -g -O2  conftest.c >&5
 configure:4158: $? = 0
 configure:4158: result: yes
 configure:4158: checking for memory.h
 configure:4158: gcc -c -g -O2  conftest.c >&5
 configure:4158: $? = 0
 configure:4158: result: yes
 configure:4158: checking for strings.h
 configure:4158: gcc -c -g -O2  conftest.c >&5
 configure:4158: $? = 0
 configure:4158: result: yes
 configure:4158: checking for inttypes.h
 configure:4158: gcc -c -g -O2  conftest.c >&5
 configure:4158: $? = 0
 configure:4158: result: yes
 configure:4158: checking for stdint.h
 configure:4158: gcc -c -g -O2  conftest.c >&5
 configure:4158: $? = 0
 configure:4158: result: yes
 configure:4158: checking for unistd.h
 configure:4158: gcc -c -g -O2  conftest.c >&5
 configure:4158: $? = 0
 configure:4158: result: yes
 configure:4172: checking minix/config.h usability
 configure:4172: gcc -c -g -O2  conftest.c >&5
 conftest.c:54:26: error: minix/config.h: No such file or directory
 configure:4172: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | /* end confdefs.h.  */
 | #include <stdio.h>
 | #ifdef HAVE_SYS_TYPES_H
 | # include <sys/types.h>
 | #endif
 | #ifdef HAVE_SYS_STAT_H
 | # include <sys/stat.h>
 | #endif
 | #ifdef STDC_HEADERS
 | # include <stdlib.h>
 | # include <stddef.h>
 | #else
 | # ifdef HAVE_STDLIB_H
 | #  include <stdlib.h>
 | # endif
 | #endif
 | #ifdef HAVE_STRING_H
 | # if !defined STDC_HEADERS && defined HAVE_MEMORY_H
 | #  include <memory.h>
 | # endif
 | # include <string.h>
 | #endif
 | #ifdef HAVE_STRINGS_H
 | # include <strings.h>
 | #endif
 | #ifdef HAVE_INTTYPES_H
 | # include <inttypes.h>
 | #endif
 | #ifdef HAVE_STDINT_H
 | # include <stdint.h>
 | #endif
 | #ifdef HAVE_UNISTD_H
 | # include <unistd.h>
 | #endif
 | #include <minix/config.h>
 configure:4172: result: no
 configure:4172: checking minix/config.h presence
 configure:4172: gcc -E  conftest.c
 conftest.c:21:26: error: minix/config.h: No such file or directory
 configure:4172: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | /* end confdefs.h.  */
 | #include <minix/config.h>
 configure:4172: result: no
 configure:4172: checking for minix/config.h
 configure:4172: result: no
 configure:4193: checking whether it is safe to define __EXTENSIONS__
 configure:4211: gcc -c -g -O2  conftest.c >&5
 configure:4211: $? = 0
 configure:4218: result: yes
 configure:4284: checking for gcc
 configure:4311: result: gcc
 configure:4540: checking for C compiler version
 configure:4549: gcc --version >&5
 gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1
 Copyright (C) 2009 Free Software Foundation, Inc.
 This is free software; see the source for copying conditions.  There is  NO
 warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR  PURPOSE.
 
 configure:4560: $? = 0
 configure:4549: gcc -v >&5
 Using built-in specs.
 Target: i486-linux-gnu
 Configured with: ../src/configure -v --with-pkgversion='Ubuntu  4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs  --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr  --enable-shared --enable-multiarch --enable-linker-build-id  --with-system-zlib --libexecdir=/usr/lib --without-included-gettext  --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4  --program-suffix=-4.4 --enable-nls --enable-clocale=gnu  --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all  --disable-werror --with-arch-32=i486 --with-tune=generic  --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu  --target=i486-linux-gnu
 Thread model: posix
 gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 
 configure:4560: $? = 0
 configure:4549: gcc -V >&5
 gcc: '-V' option must have argument
 configure:4560: $? = 1
 configure:4549: gcc -qversion >&5
 gcc: unrecognized option '-qversion'
 gcc: no input files
 configure:4560: $? = 1
 configure:4564: checking whether we are using the GNU C compiler
 configure:4592: result: yes
 configure:4601: checking whether gcc accepts -g
 configure:4662: result: yes
 configure:4679: checking for gcc option to accept ISO C89
 configure:4756: result: none needed
 configure:4778: checking dependency style of gcc
 configure:4888: result: gcc3
 configure:4904: checking whether gcc and cc understand -c and -o  together
 configure:4935: gcc -c conftest.c -o conftest2.o >&5
 configure:4939: $? = 0
 configure:4945: gcc -c conftest.c -o conftest2.o >&5
 configure:4949: $? = 0
 configure:4960: cc -c conftest.c >&5
 configure:4964: $? = 0
 configure:4972: cc -c conftest.c -o conftest2.o >&5
 configure:4976: $? = 0
 configure:4982: cc -c conftest.c -o conftest2.o >&5
 configure:4986: $? = 0
 configure:5004: result: yes
 configure:5083: checking for gcc
 configure:5099: found /usr/bin/gcc
 configure:5110: result: gcc
 configure:5135: checking for Objective C compiler version
 configure:5144: gcc --version >&5
 gcc (Ubuntu 4.4.1-4ubuntu9) 4.4.1
 Copyright (C) 2009 Free Software Foundation, Inc.
 This is free software; see the source for copying conditions.  There is  NO
 warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR  PURPOSE.
 
 configure:5155: $? = 0
 configure:5144: gcc -v >&5
 Using built-in specs.
 Target: i486-linux-gnu
 Configured with: ../src/configure -v --with-pkgversion='Ubuntu  4.4.1-4ubuntu9' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs  --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr  --enable-shared --enable-multiarch --enable-linker-build-id  --with-system-zlib --libexecdir=/usr/lib --without-included-gettext  --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4  --program-suffix=-4.4 --enable-nls --enable-clocale=gnu  --enable-libstdcxx-debug --enable-objc-gc --enable-targets=all  --disable-werror --with-arch-32=i486 --with-tune=generic  --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu  --target=i486-linux-gnu
 Thread model: posix
 gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu9) 
 configure:5155: $? = 0
 configure:5144: gcc -V >&5
 gcc: '-V' option must have argument
 configure:5155: $? = 1
 configure:5144: gcc -qversion >&5
 gcc: unrecognized option '-qversion'
 gcc: no input files
 configure:5155: $? = 1
 configure:5159: checking whether we are using the GNU Objective C  compiler
 configure:5178: gcc -c   conftest.m >&5
 gcc: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5178: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | 
 | int
 | main ()
 | {
 | #ifndef __GNUC__
 |        choke me
 | #endif
 | 
 |   ;
 |   return 0;
 | }
 configure:5187: result: no
 configure:5196: checking whether gcc accepts -g
 configure:5216: gcc -c -g  conftest.m >&5
 gcc: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5216: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | 
 | int
 | main ()
 | {
 | 
 |   ;
 |   return 0;
 | }
 configure:5231: gcc -c   conftest.m >&5
 gcc: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5231: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | 
 | int
 | main ()
 | {
 | 
 |   ;
 |   return 0;
 | }
 configure:5247: gcc -c -g  conftest.m >&5
 gcc: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5247: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | 
 | int
 | main ()
 | {
 | 
 |   ;
 |   return 0;
 | }
 configure:5257: result: no
 configure:5282: checking dependency style of gcc
 configure:5390: result: gcc3
 configure:5410: checking how to run the Objective C preprocessor
 configure:5437: gcc -E  conftest.m
 gcc: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5437: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | #ifdef __STDC__
 | # include <limits.h>
 | #else
 | # include <assert.h>
 | #endif
 |              Syntax error
 configure:5437: gcc -E  conftest.m
 gcc: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5437: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | #ifdef __STDC__
 | # include <limits.h>
 | #else
 | # include <assert.h>
 | #endif
 |              Syntax error
 configure:5437: /lib/cpp  conftest.m
 cpp: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5437: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | #ifdef __STDC__
 | # include <limits.h>
 | #else
 | # include <assert.h>
 | #endif
 |              Syntax error
 configure:5437: /lib/cpp  conftest.m
 cpp: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5437: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | #ifdef __STDC__
 | # include <limits.h>
 | #else
 | # include <assert.h>
 | #endif
 |              Syntax error
 configure:5476: result: /lib/cpp
 configure:5496: /lib/cpp  conftest.m
 cpp: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5496: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | #ifdef __STDC__
 | # include <limits.h>
 | #else
 | # include <assert.h>
 | #endif
 |              Syntax error
 configure:5496: /lib/cpp  conftest.m
 cpp: error trying to exec 'cc1obj': execvp: No such file or directory
 configure:5496: $? = 1
 configure: failed program was:
 | /* confdefs.h */
 | #define PACKAGE_NAME "techne"
 | #define PACKAGE_TARNAME "techne"
 | #define PACKAGE_VERSION "0.1"
 | #define PACKAGE_STRING "techne 0.1"
 | #define PACKAGE_BUGREPORT ""
 | #define PACKAGE_URL ""
 | #define PACKAGE "techne"
 | #define VERSION "0.1"
 | #define STDC_HEADERS 1
 | #define HAVE_SYS_TYPES_H 1
 | #define HAVE_SYS_STAT_H 1
 | #define HAVE_STDLIB_H 1
 | #define HAVE_STRING_H 1
 | #define HAVE_MEMORY_H 1
 | #define HAVE_STRINGS_H 1
 | #define HAVE_INTTYPES_H 1
 | #define HAVE_STDINT_H 1
 | #define HAVE_UNISTD_H 1
 | #define __EXTENSIONS__ 1
 | #define _ALL_SOURCE 1
 | #define _GNU_SOURCE 1
 | #define _POSIX_PTHREAD_SEMANTICS 1
 | #define _TANDEM_SOURCE 1
 | /* end confdefs.h.  */
 | #ifdef __STDC__
 | # include <limits.h>
 | #else
 | # include <assert.h>
 | #endif
 |              Syntax error
 configure:5526: error: in `/home/dave89/Downloads/techne-0.1':
 configure:5529: error: Objective C preprocessor "/lib/cpp" fails sanity  check
 See `config.log' for more details.
 
 ## ---------------- ##
 ## Cache variables. ##
 ## ---------------- ##
 
 ac_cv_c_compiler_gnu=yes
 ac_cv_env_CCC_set=
 ac_cv_env_CCC_value=
 ac_cv_env_CC_set=
 ac_cv_env_CC_value=
 ac_cv_env_CFLAGS_set=
 ac_cv_env_CFLAGS_value=
 ac_cv_env_CPPFLAGS_set=
 ac_cv_env_CPPFLAGS_value=
 ac_cv_env_CPP_set=
 ac_cv_env_CPP_value=
 ac_cv_env_CXXFLAGS_set=
 ac_cv_env_CXXFLAGS_value=
 ac_cv_env_CXX_set=
 ac_cv_env_CXX_value=
 ac_cv_env_FONTCONFIG_CFLAGS_set=
 ac_cv_env_FONTCONFIG_CFLAGS_value=
 ac_cv_env_FONTCONFIG_LIBS_set=
 ac_cv_env_FONTCONFIG_LIBS_value=
 ac_cv_env_FREETYPE_CFLAGS_set=
 ac_cv_env_FREETYPE_CFLAGS_value=
 ac_cv_env_FREETYPE_LIBS_set=
 ac_cv_env_FREETYPE_LIBS_value=
 ac_cv_env_LDFLAGS_set=
 ac_cv_env_LDFLAGS_value=
 ac_cv_env_LIBPNG_CFLAGS_set=
 ac_cv_env_LIBPNG_CFLAGS_value=
 ac_cv_env_LIBPNG_LIBS_set=
 ac_cv_env_LIBPNG_LIBS_value=
 ac_cv_env_LIBS_set=
 ac_cv_env_LIBS_value=
 ac_cv_env_LUA_CFLAGS_set=
 ac_cv_env_LUA_CFLAGS_value=
 ac_cv_env_LUA_LIBS_set=
 ac_cv_env_LUA_LIBS_value=
 ac_cv_env_OBJCFLAGS_set=
 ac_cv_env_OBJCFLAGS_value=
 ac_cv_env_OBJCPP_set=
 ac_cv_env_OBJCPP_value=
 ac_cv_env_OBJC_set=
 ac_cv_env_OBJC_value=
 ac_cv_env_OPENAL_CFLAGS_set=
 ac_cv_env_OPENAL_CFLAGS_value=
 ac_cv_env_OPENAL_LIBS_set=
 ac_cv_env_OPENAL_LIBS_value=
 ac_cv_env_PKG_CONFIG_set=
 ac_cv_env_PKG_CONFIG_value=
 ac_cv_env_XMKMF_set=
 ac_cv_env_XMKMF_value=
 ac_cv_env_build_alias_set=
 ac_cv_env_build_alias_value=
 ac_cv_env_host_alias_set=
 ac_cv_env_host_alias_value=
 ac_cv_env_target_alias_set=
 ac_cv_env_target_alias_value=
 ac_cv_header_inttypes_h=yes
 ac_cv_header_memory_h=yes
 ac_cv_header_minix_config_h=no
 ac_cv_header_stdc=yes
 ac_cv_header_stdint_h=yes
 ac_cv_header_stdlib_h=yes
 ac_cv_header_string_h=yes
 ac_cv_header_strings_h=yes
 ac_cv_header_sys_stat_h=yes
 ac_cv_header_sys_types_h=yes
 ac_cv_header_unistd_h=yes
 ac_cv_objc_compiler_gnu=no
 ac_cv_objext=o
 ac_cv_path_EGREP='/bin/grep -E'
 ac_cv_path_GREP=/bin/grep
 ac_cv_path_install='/usr/bin/install -c'
 ac_cv_path_mkdir=/bin/mkdir
 ac_cv_prog_AWK=gawk
 ac_cv_prog_CPP='gcc -E'
 ac_cv_prog_OBJCPP=/lib/cpp
 ac_cv_prog_ac_ct_CC=gcc
 ac_cv_prog_ac_ct_OBJC=gcc
 ac_cv_prog_cc_c89=
 ac_cv_prog_cc_g=yes
 ac_cv_prog_cc_gcc_c_o=yes
 ac_cv_prog_make_make_set=yes
 ac_cv_prog_objc_g=no
 ac_cv_safe_to_define___extensions__=yes
 am_cv_CC_dependencies_compiler_type=gcc3
 am_cv_OBJC_dependencies_compiler_type=gcc3
 
 ## ----------------- ##
 ## Output variables. ##
 ## ----------------- ##
 
 ACLOCAL='${SHELL} /home/dave89/Downloads/techne-0.1/missing --run  aclocal-1.11'
 AMDEPBACKSLASH='\'
 AMDEP_FALSE='#'
 AMDEP_TRUE=''
 AMTAR='${SHELL} /home/dave89/Downloads/techne-0.1/missing --run tar'
 AUTOCONF='${SHELL} /home/dave89/Downloads/techne-0.1/missing --run  autoconf'
 AUTOHEADER='${SHELL} /home/dave89/Downloads/techne-0.1/missing --run  autoheader'
 AUTOMAKE='${SHELL} /home/dave89/Downloads/techne-0.1/missing --run  automake-1.11'
 AWK='gawk'
 CC='gcc'
 CCDEPMODE='depmode=gcc3'
 CFLAGS='-g -O2'
 CPP='gcc -E'
 CPPFLAGS=''
 CXX=''
 CXXDEPMODE=''
 CXXFLAGS=''
 CYGPATH_W='echo'
 DEFS=''
 DEPDIR='.deps'
 ECHO_C=''
 ECHO_N='-n'
 ECHO_T=''
 EGREP='/bin/grep -E'
 EXEEXT=''
 FONTCONFIG_CFLAGS=''
 FONTCONFIG_LIBS=''
 FREETYPE_CFLAGS=''
 FREETYPE_LIBS=''
 GLU_CFLAGS=''
 GLU_LIBS=''
 GL_CFLAGS=''
 GL_LIBS=''
 GREP='/bin/grep'
 INSTALL_DATA='${INSTALL} -m 644'
 INSTALL_PROGRAM='${INSTALL}'
 INSTALL_SCRIPT='${INSTALL}'
 INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
 LDFLAGS=''
 LIBOBJS=''
 LIBPNG_CFLAGS=''
 LIBPNG_LIBS=''
 LIBS=''
 LTLIBOBJS=''
 LUAC=''
 LUA_CFLAGS=''
 LUA_LIBS=''
 MAKEINFO='${SHELL} /home/dave89/Downloads/techne-0.1/missing --run  makeinfo'
 MKDIR_P='/bin/mkdir -p'
 OBJC='gcc'
 OBJCDEPMODE='depmode=gcc3'
 OBJCFLAGS=''
 OBJCPP='/lib/cpp'
 OBJEXT='o'
 ODE_CFLAGS=''
 ODE_LIBS=''
 OPENAL_CFLAGS=''
 OPENAL_LIBS=''
 PACKAGE='techne'
 PACKAGE_BUGREPORT=''
 PACKAGE_NAME='techne'
 PACKAGE_STRING='techne 0.1'
 PACKAGE_TARNAME='techne'
 PACKAGE_URL=''
 PACKAGE_VERSION='0.1'
 PATH_SEPARATOR=':'
 PKG_CONFIG=''
 PTHREAD_CC=''
 PTHREAD_CFLAGS=''
 PTHREAD_LIBS=''
 SET_MAKE=''
 SHELL='/bin/bash'
 STRIP=''
 VERSION='0.1'
 XMKMF=''
 ac_ct_CC='gcc'
 ac_ct_CXX=''
 ac_ct_OBJC='gcc'
 acx_pthread_config=''
 am__EXEEXT_FALSE=''
 am__EXEEXT_TRUE=''
 am__fastdepCC_FALSE='#'
 am__fastdepCC_TRUE=''
 am__fastdepCXX_FALSE=''
 am__fastdepCXX_TRUE=''
 am__fastdepOBJC_FALSE='#'
 am__fastdepOBJC_TRUE=''
 am__include='include'
 am__isrc=''
 am__leading_dot='.'
 am__quote=''
 am__tar='${AMTAR} chof - "$$tardir"'
 am__untar='${AMTAR} xf -'
 bindir='${exec_prefix}/bin'
 build=''
 build_alias=''
 build_cpu=''
 build_os=''
 build_vendor=''
 datadir='${datarootdir}'
 datarootdir='${prefix}/share'
 docdir='${datarootdir}/doc/${PACKAGE_TARNAME}'
 dvidir='${docdir}'
 exec_prefix='NONE'
 host=''
 host_alias=''
 host_cpu=''
 host_os=''
 host_vendor=''
 htmldir='${docdir}'
 includedir='${prefix}/include'
 infodir='${datarootdir}/info'
 install_sh='${SHELL} /home/dave89/Downloads/techne-0.1/install-sh'
 libdir='${exec_prefix}/lib'
 libexecdir='${exec_prefix}/libexec'
 localedir='${datarootdir}/locale'
 localstatedir='${prefix}/var'
 mandir='${datarootdir}/man'
 mkdir_p='/bin/mkdir -p'
 oldincludedir='/usr/include'
 pdfdir='${docdir}'
 prefix='NONE'
 program_transform_name='s,x,x,'
 psdir='${docdir}'
 sbindir='${exec_prefix}/sbin'
 sharedstatedir='${prefix}/com'
 sysconfdir='${prefix}/etc'
 target_alias=''
 
 ## ----------- ##
 ## confdefs.h. ##
 ## ----------- ##
 
 /* confdefs.h */
 #define PACKAGE_NAME "techne"
 #define PACKAGE_TARNAME "techne"
 #define PACKAGE_VERSION "0.1"
 #define PACKAGE_STRING "techne 0.1"
 #define PACKAGE_BUGREPORT ""
 #define PACKAGE_URL ""
 #define PACKAGE "techne"
 #define VERSION "0.1"
 #define STDC_HEADERS 1
 #define HAVE_SYS_TYPES_H 1
 #define HAVE_SYS_STAT_H 1
 #define HAVE_STDLIB_H 1
 #define HAVE_STRING_H 1
 #define HAVE_MEMORY_H 1
 #define HAVE_STRINGS_H 1
 #define HAVE_INTTYPES_H 1
 #define HAVE_STDINT_H 1
 #define HAVE_UNISTD_H 1
 #define __EXTENSIONS__ 1
 #define _ALL_SOURCE 1
 #define _GNU_SOURCE 1
 #define _POSIX_PTHREAD_SEMANTICS 1
 #define _TANDEM_SOURCE 1
 
 configure: exit 1
```

---

