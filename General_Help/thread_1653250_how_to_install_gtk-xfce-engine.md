---
title: "how to install gtk-xfce-engine?"
date: 2010-12-26
forum: General Help
---

### Post by princeofnam on 2010-12-26
I had an interest in installing this theme [http://gnome-look.org/content/show.php/Royalty?content=67866](http://gnome-look.org/content/show.php/Royalty?content=67866)
but it requres gtk-xfc-engine.  I found the compressed package but I'm not sure how to install it?

---

### Post by karthick87 on 2010-12-26
Untar the file first and from the directory run,
```
./configure
```
```
make
```
```
make install
```

---

### Post by princeofnam on 2010-12-26
After that do the files automatically install into my system, leaving the files i make, make installed deletable?  Or must I keep the files i make, make installed?

---

### Post by princeofnam on 2010-12-26
also running make and make install didn't work

[email]sushi@Ragnarork:~/.themes[/email]/gtk-xfce-engine-2.2.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
[email]sushi@Ragnarork:~/.themes[/email]/gtk-xfce-engine-2.2.1$ make
make: *** No targets specified and no makefile found.  Stop.
[email]sushi@Ragnarork:~/.themes[/email]/gtk-xfce-engine-2.2.1$ make install
make: *** No rule to make target `install'.  Stop.
[email]sushi@Ragnarork:~/.themes[/email]/gtk-xfce-engine-2.2.1$

---

### Post by princeofnam on 2010-12-26
I'm guessing I need a C++ compiler.  Does anyone know where I can find that in ubuntu?

---

### Post by princeofnam on 2010-12-26
well after I installed build-essential it still wouldn't work.  how irritating

[qupte]sushi@Ragnarork:~/.themes/gtk-xfce-engine-2.2.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for inline... inline
checking for an ANSI C-conforming const... yes
checking for X... no
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0... Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (glib-2.0 >= 2.0.0 gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
[email]sushi@Ragnarork:~/.themes[/email]/gtk-xfce-engine-2.2.1$ make
make: *** No targets specified and no makefile found.  Stop.
[email]sushi@Ragnarork:~/.themes[/email]/gtk-xfce-engine-2.2.1$ make install
make: *** No rule to make target `install'.  Stop.
[email]sushi@Ragnarork:~/.themes[/email]/gtk-xfce-engine-2.2.1$ ^C
[email]sushi@Ragnarork:~/.themes[/email]/gtk-xfce-engine-2.2.1$ 
[/quote]

---

### Post by hhh on 2010-12-26
Woah woah woah! He must mean gtk2-engines-xfce...
[http://packages.ubuntu.com/maverick/gtk2-engines-xfce](http://packages.ubuntu.com/maverick/gtk2-engines-xfce)

Open a terminal and run...```
sudp apt-get install gtk2-engines-xfce
```
I'll install this theme to make sure and post back, hope that helps!

---

### Post by hhh on 2010-12-26
Yes...

[[IMG]http://img89.imageshack.us/img89/4069/screenshot1226201007334.th.png[/IMG]](http://img89.imageshack.us/img89/4069/screenshot1226201007334.png)

---

### Post by princeofnam on 2010-12-26
haha thanks

---

### Post by hhh on 2010-12-26
No problem.

---

