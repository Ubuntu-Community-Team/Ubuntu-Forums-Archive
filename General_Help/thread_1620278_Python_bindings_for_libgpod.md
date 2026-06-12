---
title: "Python bindings for libgpod"
date: 2010-11-12
forum: General Help
---

### Post by Timtro on 2010-11-12
Hi All,

Thanks in advance. I hope I'm not just doing something silly (or missing the obvious).

Despite having met the following dependencies:
```

* Packages required to build python bindings

On Debian the following packages are required:

python (e.g. python2.4)
python-dev (e.g. python2.4-dev)
python-mutagen

These are needed for full photo/thumbnail support:
python-gtk2-dev (and python-gobject-dev, if using python-gtk2-dev >= 2.10)

```

I cannot get libgpod's configure script (0.8.0, fresh from Sourceforge) to let it get built. There is no apparent reason, it just says in the summary at the end 'no'.

```

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking how to print strings... printf
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for ANSI C header files... (cached) yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking whether NLS is requested... yes
checking for intltool >= 0.21... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for XML::Parser... ok
checking for localtime_r... yes
checking for struct tm.tm_gmtoff... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBGPOD... yes
checking for GLIB... yes
checking for sg_ll_inquiry in -lsgutils2... no
checking for sg_ll_inquiry in -lsgutils... no
checking for LIBUSB... no
checking for inflate in -lz... yes
checking for HAL... yes
checking for LIBIMOBILEDEVICE... no
checking for TAGLIB... no
checking for LIBXML... yes
checking for GDKPIXBUF... yes
checking for PYGOBJECT... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  de es fr he it ja ro sv zh_CN
checking for gtkdoc-check... /usr/bin/gtkdoc-check
checking for gtkdoc-rebase... /usr/bin/gtkdoc-rebase
checking for gtkdoc-mkpdf... /usr/bin/gtkdoc-mkpdf
checking whether to build gtk-doc documentation... no
checking whether to build python bindings... yes
checking for python... /usr/bin/python
checking whether /usr/bin/python version >= 2.1.1... yes
checking for /usr/bin/python version... 2.6
checking for /usr/bin/python platform... linux2
checking for /usr/bin/python script directory... ${prefix}/lib/python2.6/dist-packages
checking for /usr/bin/python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
checking for python development headers... found
checking for python module mutagen >= 1.8... yes
checking for swig... no
checking whether to build mono bindings... auto
checking for MONO_MODULE... no
checking for gmcs... /usr/bin/gmcs
checking for mono... /usr/bin/mono
checking for GDKSHARP... no
checking for GLIBSHARP... no
checking for more warnings... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating bindings/Makefile
config.status: creating bindings/mono/Makefile
config.status: creating bindings/mono/libgpod-sharp/libgpod-sharp.pc
config.status: creating bindings/mono/libgpod-sharp/Makefile
config.status: creating bindings/mono/libgpod-sharp-test/Makefile
config.status: creating bindings/mono/libgpod-sharp-test/libgpod-sharp-test
config.status: creating bindings/python/gpod.i
config.status: creating bindings/python/Makefile
config.status: creating bindings/python/examples/Makefile
config.status: creating bindings/python/tests/Makefile
config.status: creating docs/Makefile
config.status: creating docs/reference/Makefile
config.status: creating docs/reference/version.xml
config.status: creating m4/Makefile
config.status: creating po/Makefile.in
config.status: creating src/Makefile
config.status: creating tools/Makefile
config.status: creating tests/Makefile
config.status: creating libgpod-1.0.pc
config.status: creating tools/90-libgpod.rules
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing libtool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

Configuration for libgpod 0.8.0 :
--------------------------------

 Host System Type .........: x86_64-unknown-linux-gnu
 Install path .............: /usr/local
 Preprocessor .............: gcc 
 Compiler .................: gcc -g -O2 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2   -I/usr/include/libxml2   -pthread -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
 Linker ...................: gcc   -pthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0 -lsqlite3 -lplist   -lxml2   -pthread -lgdk_pixbuf-2.0 -lm -lgobject-2.0 -lgmodule-2.0 -lpng12 -lgthread-2.0 -lrt -lglib-2.0  
 Artwork support ..........: yes
 Mono bindings ............: no
 Python bindings ..........: no
 PyGObject support ........: yes
 iPhone/iPod Touch support.: no
 Temporary mount directory.: /tmp/

 Now type 'make' to build libgpod 0.8.0,
 and then 'make install' for installation.

```

Any ideas? Am I missing something stupid?

---

### Post by noviante on 2011-11-13
I don't know if you've already resolved this for yourself yet or not, but in looking at your log output, you need to install swig.  The relevant lines in your output:

> checking whether to build python bindings... yes
checking for python... /usr/bin/python
checking whether /usr/bin/python version >= 2.1.1... yes
checking for /usr/bin/python version... 2.6
checking for /usr/bin/python platform... linux2
checking for /usr/bin/python script directory... ${prefix}/lib/python2.6/dist-packages
checking for /usr/bin/python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
checking for python development headers... found
checking for python module mutagen >= 1.8... yes
**checking for swig... no**I'm a debian user, so I don't know the exact Ubuntu package name for this.  In debian, it's simply 'swig'.

Happy source building!

---

