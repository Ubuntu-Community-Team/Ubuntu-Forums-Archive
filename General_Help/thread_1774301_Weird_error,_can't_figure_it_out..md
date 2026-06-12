---
title: "Weird error, can't figure it out."
date: 2011-06-03
forum: General Help
---

### Post by elitejarod on 2011-06-03
I am trying to ./configure epiar a game I downloaded the source to.  I can't seem to stop getting this error at the bottom of the ./configure script, and it doesn't make any sense because I have libxml2 installed, I've tried to even --reinstall all the libxmls that are on my system to no avail.  What the hell is wrong with this?  Why doesn't it see the obvious library I HAVE?

Help a brotha out?

```
~/Downloads/epiar-0.4.2$ tar -xvzf libxml2-sources-2.6.29.tar.gz
tar (child): libxml2-sources-2.6.29.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
jarod@jarod-GT5670:~/Downloads/epiar-0.4.2$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ranlib... ranlib
checking for xml2-config... /usr/bin/xml2-config
checking for libxml - version >= 2.4.0... no
*** Could not run libxml test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means LIBXML was incorrectly installed
*** or that you have moved LIBXML since it was installed. In the latter case, you
*** may want to edit the xml2-config script: /usr/bin/xml2-config
configure: error: Cannot find XML2: Is xml2-config in path?
jarod@jarod-GT5670:~/Downloads/epiar-0.4.2$ sudo apt-get install build-essential libxml2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
libxml2-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
 
```

---

### Post by elitejarod on 2011-06-03
Actually figured out the above error, but ran into another one right after it.  Code below.

Any help would be appreciated.

Wierd thing is I have sdl 1.2.14 which is a more improved version than 1.2.10 and it doesn't seem to get that I have it.

```
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ranlib... ranlib
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for FTGL... yes
checking for libxml2... yes
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.10... no
*** Could not run SDL test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means SDL was incorrectly installed
*** or that you have moved SDL since it was installed. In the latter case, you
*** may want to edit the sdl-config script: /usr/bin/sdl-config
configure: error: *** SDL version 1.2.10 not found!
```

---

### Post by oldos2er on 2011-06-03
Which version of Ubuntu are you running? Did you run ./autogen.sh before ./configure? I followed the instructions here, and it worked: [http://epiar.net/trac/wiki/BuildingEpiarOnUbuntu](http://epiar.net/trac/wiki/BuildingEpiarOnUbuntu)

---

### Post by elitejarod on 2011-06-03
> **oldos2er said:**
> Which version of Ubuntu are you running? Did you run ./autogen.sh before ./configure? I followed the instructions here, and it worked: [http://epiar.net/trac/wiki/BuildingEpiarOnUbuntu](http://epiar.net/trac/wiki/BuildingEpiarOnUbuntu)
newest version 11.04 and I did run ./autogen.sh before it.  Still getting the error.

here is a copy of the config.log if that helps.

> This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by configure, which was
generated by GNU Autoconf 2.67.  Invocation command line was

  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = jarod-GT5670
uname -m = i686
uname -r = 2.6.38-8-generic
uname -s = Linux
uname -v = #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011

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

configure:2030: checking build system type
configure:2044: result: i686-pc-linux-gnu
configure:2064: checking host system type
configure:2077: result: i686-pc-linux-gnu
configure:2097: checking target system type
configure:2110: result: i686-pc-linux-gnu
configure:2153: checking for a BSD-compatible install
configure:2221: result: /usr/bin/install -c
configure:2232: checking whether build environment is sane
configure:2282: result: yes
configure:2423: checking for a thread-safe mkdir -p
configure:2462: result: /bin/mkdir -p
configure:2475: checking for gawk
configure:2505: result: no
configure:2475: checking for mawk
configure:2491: found /usr/bin/mawk
configure:2502: result: mawk
configure:2513: checking whether make sets $(MAKE)
configure:2535: result: yes
configure:2630: checking for style of include used by make
configure:2658: result: GNU
configure:2728: checking for gcc
configure:2744: found /usr/bin/gcc
configure:2755: result: gcc
configure:2984: checking for C compiler version
configure:2993: gcc --version >&5
gcc (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3004: $? = 0
configure:2993: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
configure:3004: $? = 0
configure:2993: gcc -V >&5
gcc: '-V' option must have argument
configure:3004: $? = 1
configure:2993: gcc -qversion >&5
gcc: unrecognized option '-qversion'
gcc: no input files
configure:3004: $? = 1
configure:3024: checking whether the C compiler works
configure:3046: gcc    conftest.c  >&5
configure:3050: $? = 0
configure:3098: result: yes
configure:3101: checking for C compiler default output file name
configure:3103: result: a.out
configure:3109: checking for suffix of executables
configure:3116: gcc -o conftest    conftest.c  >&5
configure:3120: $? = 0
configure:3142: result: 
configure:3164: checking whether we are cross compiling
configure:3172: gcc -o conftest    conftest.c  >&5
configure:3176: $? = 0
configure:3183: ./conftest
configure:3187: $? = 0
configure:3202: result: no
configure:3207: checking for suffix of object files
configure:3229: gcc -c   conftest.c >&5
configure:3233: $? = 0
configure:3254: result: o
configure:3258: checking whether we are using the GNU C compiler
configure:3277: gcc -c   conftest.c >&5
configure:3277: $? = 0
configure:3286: result: yes
configure:3295: checking whether gcc accepts -g
configure:3315: gcc -c -g  conftest.c >&5
configure:3315: $? = 0
configure:3356: result: yes
configure:3373: checking for gcc option to accept ISO C89
configure:3437: gcc  -c -g -O2  conftest.c >&5
configure:3437: $? = 0
configure:3450: result: none needed
configure:3472: checking dependency style of gcc
configure:3582: result: gcc3
configure:3602: checking how to run the C preprocessor
configure:3633: gcc -E  conftest.c
configure:3633: $? = 0
configure:3647: gcc -E  conftest.c
conftest.c:11:28: fatal error: ac_nonexistent.h: No such file or directory
compilation terminated.
configure:3647: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| #define PACKAGE ""
| #define VERSION ""
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3672: result: gcc -E
configure:3692: gcc -E  conftest.c
configure:3692: $? = 0
configure:3706: gcc -E  conftest.c
conftest.c:11:28: fatal error: ac_nonexistent.h: No such file or directory
compilation terminated.
configure:3706: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| #define PACKAGE ""
| #define VERSION ""
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3792: checking for g++
configure:3808: found /usr/bin/g++
configure:3819: result: g++
configure:3846: checking for C++ compiler version
configure:3855: g++ --version >&5
g++ (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3866: $? = 0
configure:3855: g++ -v >&5
Using built-in specs.
COLLECT_GCC=g++
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
configure:3866: $? = 0
configure:3855: g++ -V >&5
g++: '-V' option must have argument
configure:3866: $? = 1
configure:3855: g++ -qversion >&5
g++: unrecognized option '-qversion'
g++: no input files
configure:3866: $? = 1
configure:3870: checking whether we are using the GNU C++ compiler
configure:3889: g++ -c   conftest.cpp >&5
configure:3889: $? = 0
configure:3898: result: yes
configure:3907: checking whether g++ accepts -g
configure:3927: g++ -c -g  conftest.cpp >&5
configure:3927: $? = 0
configure:3968: result: yes
configure:3993: checking dependency style of g++
configure:4103: result: gcc3
configure:4166: checking for gcc
configure:4193: result: gcc
configure:4422: checking for C compiler version
configure:4431: gcc --version >&5
gcc (Ubuntu/Linaro 4.5.2-8ubuntu4) 4.5.2
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:4442: $? = 0
configure:4431: gcc -v >&5
Using built-in specs.
COLLECT_GCC=gcc
COLLECT_LTO_WRAPPER=/usr/lib/i386-linux-gnu/gcc/i686-linux-gnu/4.5.2/lto-wrapper
Target: i686-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu/Linaro 4.5.2-8ubuntu4' --with-bugurl=file:///usr/share/doc/gcc-4.5/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --program-suffix=-4.5 --enable-shared --enable-multiarch --with-multiarch-defaults=i386-linux-gnu --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib/i386-linux-gnu --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.5 --libdir=/usr/lib/i386-linux-gnu --enable-nls --with-sysroot=/ --enable-clocale=gnu --enable-libstdcxx-debug --enable-libstdcxx-time=yes --enable-plugin --enable-gold --enable-ld=default --with-plugin-ld=ld.gold --enable-objc-gc --enable-targets=all --disable-werror --with-arch-32=i686 --with-tune=generic --enable-checking=release --build=i686-linux-gnu --host=i686-linux-gnu --target=i686-linux-gnu
Thread model: posix
gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
configure:4442: $? = 0
configure:4431: gcc -V >&5
gcc: '-V' option must have argument
configure:4442: $? = 1
configure:4431: gcc -qversion >&5
gcc: unrecognized option '-qversion'
gcc: no input files
configure:4442: $? = 1
configure:4446: checking whether we are using the GNU C compiler
configure:4474: result: yes
configure:4483: checking whether gcc accepts -g
configure:4544: result: yes
configure:4561: checking for gcc option to accept ISO C89
configure:4638: result: none needed
configure:4660: checking dependency style of gcc
configure:4770: result: gcc3
configure:4828: checking for ranlib
configure:4844: found /usr/bin/ranlib
configure:4855: result: ranlib
configure:4958: checking for pkg-config
configure:4976: found /usr/bin/pkg-config
configure:4988: result: /usr/bin/pkg-config
configure:5013: checking pkg-config is at least version 0.9.0
configure:5016: result: yes
configure:5026: checking for FTGL
configure:5033: $PKG_CONFIG --exists --print-errors "ftgl >= 2.1.3"
configure:5036: $? = 0
configure:5049: $PKG_CONFIG --exists --print-errors "ftgl >= 2.1.3"
configure:5052: $? = 0
configure:5109: result: yes
configure:5121: checking for libxml2
configure:5128: $PKG_CONFIG --exists --print-errors "libxml-2.0 >= 2.7.6"
configure:5131: $? = 0
configure:5144: $PKG_CONFIG --exists --print-errors "libxml-2.0 >= 2.7.6"
configure:5147: $? = 0
configure:5204: result: yes
configure:5259: checking for sdl-config
configure:5277: found /usr/bin/sdl-config
configure:5290: result: /usr/bin/sdl-config
configure:5299: checking for SDL - version >= 1.2.10
configure:5386: g++ -o conftest -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   conftest.cpp  -lphysfs -lftgl   -lxml2   -L/usr/lib -lSDL >&5
conftest.cpp: In function 'int main(int, char**)':
conftest.cpp:44:35: warning: deprecated conversion from string constant to 'char*'
/usr/bin/ld: cannot find -lphysfs
collect2: ld returned 1 exit status
configure:5386: $? = 1
configure: program exited with status 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| #define PACKAGE ""
| #define VERSION ""
| /* end confdefs.h.  */
| 
| #include <stdio.h>
| #include <stdlib.h>
| #include <string.h>
| #include "SDL.h"
| 
| char*
| my_strdup (char *str)
| {
|   char *new_str;
| 
|   if (str)
|     {
|       new_str = (char *)malloc ((strlen (str) + 1) * sizeof(char));
|       strcpy (new_str, str);
|     }
|   else
|     new_str = NULL;
| 
|   return new_str;
| }
| 
| int main (int argc, char *argv[])
| {
|   int major, minor, micro;
|   char *tmp_version;
| 
|   /* This hangs on some systems (?)
|   system ("touch conf.sdltest");
|   */
|   { FILE *fp = fopen("conf.sdltest", "a"); if ( fp ) fclose(fp); }
| 
|   /* HP/UX 9 (%@#!) writes to sscanf strings */
|   tmp_version = my_strdup("1.2.10");
|   if (sscanf(tmp_version, "%d.%d.%d", &major, &minor, &micro) != 3) {
|      printf("%s, bad version string\n", "1.2.10");
|      exit(1);
|    }
| 
|    if ((1 > major) ||
|       ((1 == major) && (2 > minor)) ||
|       ((1 == major) && (2 == minor) && (14 >= micro)))
|     {
|       return 0;
|     }
|   else
|     {
|       printf("\n*** 'sdl-config --version' returned %d.%d.%d, but the minimum version\n", 1, 2, 14);
|       printf("*** of SDL required is %d.%d.%d. If sdl-config is correct, then it is\n", major, minor, micro);
|       printf("*** best to upgrade to the required version.\n");
|       printf("*** If sdl-config was wrong, set the environment variable SDL_CONFIG\n");
|       printf("*** to point to the correct copy of sdl-config, and remove the file\n");
|       printf("*** config.cache before re-running configure\n");
|       return 1;
|     }
| }
| 
| 
configure:5405: result: no
configure:5439: g++ -o conftest -g -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT   conftest.cpp  -lphysfs -lftgl   -lxml2   -L/usr/lib -lSDL >&5
/usr/bin/ld: cannot find -lphysfs
collect2: ld returned 1 exit status
configure:5439: $? = 1
configure: failed program was:
| /* confdefs.h */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE_URL ""
| #define PACKAGE ""
| #define VERSION ""
| /* end confdefs.h.  */
| 
| #include <stdio.h>
| #include "SDL.h"
| 
| int main(int argc, char *argv[])
| { return 0; }
| #undef  main
| #define main K_and_R_C_main
| 
| int
| main ()
| {
|  return 0;
|   ;
|   return 0;
| }
configure:5464: error: *** SDL version 1.2.10 not found!

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_cxx_compiler_gnu=yes
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
ac_cv_env_FTGL_CFLAGS_set=
ac_cv_env_FTGL_CFLAGS_value=
ac_cv_env_FTGL_LIBS_set=
ac_cv_env_FTGL_LIBS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_LIBS_set=
ac_cv_env_LIBS_value=
ac_cv_env_PKG_CONFIG_LIBDIR_set=
ac_cv_env_PKG_CONFIG_LIBDIR_value=
ac_cv_env_PKG_CONFIG_PATH_set=
ac_cv_env_PKG_CONFIG_PATH_value=
ac_cv_env_PKG_CONFIG_set=
ac_cv_env_PKG_CONFIG_value=
ac_cv_env_SDL_image_CFLAGS_set=
ac_cv_env_SDL_image_CFLAGS_value=
ac_cv_env_SDL_image_LIBS_set=
ac_cv_env_SDL_image_LIBS_value=
ac_cv_env_SDL_mixer_CFLAGS_set=
ac_cv_env_SDL_mixer_CFLAGS_value=
ac_cv_env_SDL_mixer_LIBS_set=
ac_cv_env_SDL_mixer_LIBS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_libxml2_CFLAGS_set=
ac_cv_env_libxml2_CFLAGS_value=
ac_cv_env_libxml2_LIBS_set=
ac_cv_env_libxml2_LIBS_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_host=i686-pc-linux-gnu
ac_cv_objext=o
ac_cv_path_SDL_CONFIG=/usr/bin/sdl-config
ac_cv_path_ac_pt_PKG_CONFIG=/usr/bin/pkg-config
ac_cv_path_install='/usr/bin/install -c'
ac_cv_path_mkdir=/bin/mkdir
ac_cv_prog_AWK=mawk
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_CXX=g++
ac_cv_prog_ac_ct_RANLIB=ranlib
ac_cv_prog_cc_c89=
ac_cv_prog_cc_g=yes
ac_cv_prog_cxx_g=yes
ac_cv_prog_make_make_set=yes
ac_cv_target=i686-pc-linux-gnu
am_cv_CC_dependencies_compiler_type=gcc3
am_cv_CXX_dependencies_compiler_type=gcc3
pkg_cv_FTGL_CFLAGS='-I/usr/include/freetype2 -I/usr/include/FTGL  '
pkg_cv_FTGL_LIBS='-lftgl  '
pkg_cv_libxml2_CFLAGS='-I/usr/include/libxml2  '
pkg_cv_libxml2_LIBS='-lxml2  '

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/jarod/Downloads/Epiar/missing --run aclocal-1.11'
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/jarod/Downloads/Epiar/missing --run tar'
AUTOCONF='${SHELL} /home/jarod/Downloads/Epiar/missing --run autoconf'
AUTOHEADER='${SHELL} /home/jarod/Downloads/Epiar/missing --run autoheader'
AUTOMAKE='${SHELL} /home/jarod/Downloads/Epiar/missing --run automake-1.11'
AWK='mawk'
CC='gcc'
CCDEPMODE='depmode=gcc3'
CFLAGS='-g -O2 -DUSE_PHYSICSFS -I/usr/include/ -I/usr/include/freetype2 -I/usr/include/FTGL   -I/usr/include/libxml2  '
CPP='gcc -E'
CPPFLAGS=''
CXX='g++'
CXXDEPMODE='depmode=gcc3'
CXXFLAGS='-g -O2'
CYGPATH_W='echo'
DEFS=''
DEPDIR='.deps'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EXEEXT=''
FTGL_CFLAGS='-I/usr/include/freetype2 -I/usr/include/FTGL  '
FTGL_LIBS='-lftgl  '
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='$(install_sh) -c -s'
LDFLAGS=''
LIBOBJS=''
LIBS=' -lphysfs -lftgl   -lxml2  '
LTLIBOBJS=''
MAKEINFO='${SHELL} /home/jarod/Downloads/Epiar/missing --run makeinfo'
MKDIR_P='/bin/mkdir -p'
OBJEXT='o'
PACKAGE=''
PACKAGE_BUGREPORT=''
PACKAGE_NAME=''
PACKAGE_STRING=''
PACKAGE_TARNAME=''
PACKAGE_URL=''
PACKAGE_VERSION=''
PATH_SEPARATOR=':'
PKG_CONFIG='/usr/bin/pkg-config'
PKG_CONFIG_LIBDIR=''
PKG_CONFIG_PATH=''
RANLIB='ranlib'
SDL_CFLAGS=''
SDL_CONFIG='/usr/bin/sdl-config'
SDL_LIBS=''
SDL_image_CFLAGS=''
SDL_image_LIBS=''
SDL_mixer_CFLAGS=''
SDL_mixer_LIBS=''
SET_MAKE=''
SHELL='/bin/bash'
STRIP=''
VERSION=''
ac_ct_CC='gcc'
ac_ct_CXX='g++'
am__EXEEXT_FALSE=''
am__EXEEXT_TRUE=''
am__fastdepCC_FALSE='#'
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE='#'
am__fastdepCXX_TRUE=''
am__include='include'
am__isrc=''
am__leading_dot='.'
am__quote=''
am__tar='${AMTAR} chof - "$$tardir"'
am__untar='${AMTAR} xf -'
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${datarootdir}'
datarootdir='${prefix}/share'
docdir='${datarootdir}/doc/${PACKAGE}'
dvidir='${docdir}'
exec_prefix='NONE'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
htmldir='${docdir}'
includedir='${prefix}/include'
infodir='${datarootdir}/info'
install_sh='${SHELL} /home/jarod/Downloads/Epiar/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
libxml2_CFLAGS='-I/usr/include/libxml2  '
libxml2_LIBS='-lxml2  '
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
target='i686-pc-linux-gnu'
target_alias=''
target_cpu='i686'
target_os='linux-gnu'
target_vendor='pc'

## ----------- ##
## confdefs.h. ##
## ----------- ##

/* confdefs.h */
#define PACKAGE_NAME ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define PACKAGE_STRING ""
#define PACKAGE_BUGREPORT ""
#define PACKAGE_URL ""
#define PACKAGE ""
#define VERSION ""

configure: exit 1

---

