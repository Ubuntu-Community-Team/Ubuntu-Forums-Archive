---
title: "zeitgeist-datasources error: libxul 1.92 for firefox-36-libzg"
date: 2012-08-07
forum: General Help
---

### Post by doclinux on 2012-08-07
I have been trying to get zeitgeist installed on Ubuntu 12.04 lts for about a 2 month now  reading every where with no luck getting it to build from trunk. I need  help 

I have installed every thing that ubuntu,s repo. have with  synaptic  now. but still can not get the zeitgeist-datasources to build, i get   error: libxul 1.92 for firefox-36-libzg not found.  i have the  uxlruner-1.9.2 at /opt/xulrunner/1.9.2 and ran ./xulrunner  --register-global.

Then at the build trunk:

~/buld/zeitgeist-datasources$ ./autogen.sh --enable-all-plugins
/usr/bin/autoreconf
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./config.guess'
libtoolize: copying file `./config.sub'
libtoolize: copying file `./install-sh'
libtoolize: copying file `./ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
Running ./configure --enable-all-plugins ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert i686-pc-linux-gnu file names to i686-pc-linux-gnu format... func_convert_file_noop
checking how to convert i686-pc-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking for ANSI C header files... (cached) yes
checking for valac... /usr/bin/valac
checking /usr/bin/valac is at least version 0.7.10... yes
checking pkg-config is at least version 0.9.0... yes
checking for ZEITGEIST... yes
checking for GTK... yes
configure: Requested to enable all plugins: yes
checking for dmcs... /usr/bin/dmcs
checking for GEANY... yes
checking for emacs... emacs
checking where .elc files should go... ${datarootdir}/emacs/site-lisp
checking for ZEITGEIST_SHARP... yes
checking for TOMBOY_ADDINS... yes
checking for GTK_SHARP... yes
checking for tomboy... /usr/bin/tomboy
checking for LIBXUL_1_9_2... no
configure: error: libxul 1.92 for firefox-36-libzg not found

......................................

I do have the old version of xulruner (eg..  xulrunner-1.9.2.en-US.linux-i686.tar.bz2) installed,  not   xulrunner-3.6.26.en-US.linux-i686.tar.bz2.. I had installed 3.6.26 but  it did not work so i ./xulrunner --unregister-global  then installed  1.9.2 and still did not build.

so please help I'm trying to get zeitgeist to record every thing i can  especially, firefox and chat programs for a friend thanks 
David

---

### Post by doclinux on 2012-08-08
Do i have this post in thé right froum??? 

I need to fix this so please help.

---

