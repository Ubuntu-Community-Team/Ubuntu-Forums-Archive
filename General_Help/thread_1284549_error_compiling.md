---
title: "error compiling"
date: 2009-10-06
forum: General Help
---

### Post by 21stylecrew on 2009-10-06
Hi all,
yesterday I tried to compile and install a new version of gnome-panel.
when I write "make",it was show me this problem.

>    	 	 	 	 	 	  gonza@WhiteWind:~$ cd ~/gnome-panel
 

 gonza@WhiteWind:~/gnome-panel$ ./configure
 

 checking for a BSD-compatible install... /usr/bin/install -c
 

 checking whether build environment is sane... yes
 

 checking for a thread-safe mkdir -p... /bin/mkdir -p
 

 checking for gawk... no
 

 checking for mawk... mawk
 

 checking whether make sets $(MAKE)... yes
 

 checking whether to enable maintainer-specific portions of Makefiles... no
 

 checking whether NLS is requested... yes
 

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
 

 checking for intltool >= 0.40.0... 0.40.6 found
 

 checking for intltool-update... /usr/bin/intltool-update
 

 checking for intltool-merge... /usr/bin/intltool-merge
 

 checking for intltool-extract... /usr/bin/intltool-extract
 

 checking for xgettext... /usr/bin/xgettext
 

 checking for msgmerge... /usr/bin/msgmerge
 

 checking for msgfmt... /usr/bin/msgfmt
 

 checking for gmsgfmt... /usr/bin/msgfmt
 

 checking for perl... /usr/bin/perl
 

 checking for XML::Parser... ok
 

 checking for library containing strerror... none required
 

 checking for gcc... (cached) gcc
 

 checking whether we are using the GNU C compiler... (cached) yes
 

 checking whether gcc accepts -g... (cached) yes
 

 checking for gcc option to accept ISO C89... (cached) none needed
 

 checking dependency style of gcc... (cached) gcc3
 

 checking how to run the C preprocessor... gcc -E
 

 checking for grep that handles long lines and -e... /bin/grep
 

 checking for egrep... /bin/grep -E
 

 checking for ANSI C header files... yes
 

 checking build system type... i686-pc-linux-gnu
 

 checking host system type... i686-pc-linux-gnu
 

 checking for a sed that does not truncate output... /bin/sed
 

 checking for fgrep... /bin/grep -F
 

 checking for ld used by gcc... /usr/bin/ld
 

 checking if the linker (/usr/bin/ld) is GNU ld... yes
 

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
 

 checking whether gcc and cc understand -c and -o together... yes
 

 checking for python... /usr/bin/python
 

 checking for python version... 2.6
 

 checking for python platform... linux2
 

 checking for python script directory... ${prefix}/lib/python2.6/dist-packages
 

 checking for python extension module directory... ${exec_prefix}/lib/python2.6/dist-packages
 

 checking for glib-genmarshal... /usr/bin/glib-genmarshal
 

 checking for gconftool-2... /usr/bin/gconftool-2
 

 checking whether gcc understands -Wno-sign-compare... yes
 

 checking what warning flags to pass to the C compiler... -Wall -Wmissing-prototypes -Wnested-externs -Wpointer-arith -Wno-sign-compare
 

 checking what language compliance flags to pass to the C compiler...  
 

 checking crt_externs.h usability... no
 

 checking crt_externs.h presence... no
 

 checking for crt_externs.h... no
 

 checking for _NSGetEnviron... no
 

 checking for pkg-config... /usr/bin/pkg-config
 

 checking pkg-config is at least version 0.9.0... yes
 

 checking for PANEL... configure: error: Package requirements (ORBit-2.0 >= 2.4.0 gdk-pixbuf-2.0 >= 2.7.1 pango >= 1.15.4 gtk+-2.0 >= 2.15.1 glib-2.0 >= 2.18.0 gio-2.0 >= 2.18.0 gio-unix-2.0 >= 2.18.0 libgnome-2.0 >= 2.13.0 libgnomeui-2.0 >= 2.5.4 libbonoboui-2.0 >= 2.1.1 gnome-desktop-2.0 >= 2.11.1 gconf-2.0 >= 2.6.1 libgnome-menu >= 2.27.92 dbus-glib-1 >= 0.60) were not met:
 

 

 

 No package 'ORBit-2.0' found
 

 No package 'libgnome-2.0' found
 

 No package 'libgnomeui-2.0' found
 

 No package 'libbonoboui-2.0' found
 

 No package 'gnome-desktop-2.0' found
 

 No package 'gconf-2.0' found
 

 No package 'libgnome-menu' found
 

 No package 'dbus-glib-1' found
 

 

 

 Consider adjusting the PKG_CONFIG_PATH environment variable if you
 

 installed software in a non-standard prefix.
 

 

 

 Alternatively, you may set the environment variables PANEL_CFLAGS
 

 and PANEL_LIBS to avoid the need to call pkg-config.
 

 See the pkg-config man page for more details.
 

 

 

 gonza@WhiteWind:~/gnome-panel$ make
 

 make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
 

 gonza@WhiteWind:~/gnome-panel$ make intall
 

 make: *** No hay ninguna regla para construir el objetivo `intall'.  Alto.
 

 gonza@WhiteWind:~/gnome-panel$ make install
 

 make: *** No hay ninguna regla para construir el objetivo `install'.  Alto.
 

 gonza@WhiteWind:~/gnome-panel$  
 

 

Anybody know where is the problem???

thank u

---

### Post by oldos2er on 2009-10-06
No package 'ORBit-2.0' found
   No package 'libgnome-2.0' found
   No package 'libgnomeui-2.0' found
   No package 'libbonoboui-2.0' found
   No package 'gnome-desktop-2.0' found
   No package 'gconf-2.0' found
   No package 'libgnome-menu' found
   No package 'dbus-glib-1' found

 Those are dependencies you need to install (the -dev versions) to successfully compile the software. See [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by beastrace91 on 2009-10-06
Do the following to grab everything you need to compile it: ```
sudo apt-get build-dep gnome-panel
```

~Jeff

---

