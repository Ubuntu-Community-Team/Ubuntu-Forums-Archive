---
title: "Problems compiling Banshee"
date: 2009-08-19
forum: General Help
---

### Post by Yansky on 2009-08-19
I'm trying to compile the <a href="http://banshee-project.org/download/archives/1.5.0/">latest beta of Banshee</a>, but I keep running into an error with the GTK library. I have both libgtk2.0-0 & gtk-sharp2 installed, but I keep getting the following error message:
```
yansky@ubuntu-desktop:~$ cd /home/yansky/banshee
yansky@ubuntu-desktop:~/banshee$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking for intltool >= 0.35.0... 0.40.6 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
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
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.16... yes
checking for GLIB - version >= 2.0.0... no
 *** Could not run GLIB test program, checking why...
 *** The test program failed to compile or link. See the file config.log for the
 *** exact error that occured. This usually means GLIB is incorrectly installed.
checking for GTK... configure: error: Package requirements (gtk+-2.0 >= 2.8) were not met:
  
No package 'gtk+-2.0' found
  
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
  
Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
  
yansky@ubuntu-desktop:~/banshee$ 
```

---

### Post by ithinkitschad on 2009-08-19
... How come you dont "sudo apt-get install banshee"

---

### Post by ithinkitschad on 2009-08-19
My bad I didnt see that it was beta.

---

### Post by nikhilk on 2009-08-19
> **Yansky said:**
> I have both libgtk2.0-0 & gtk-sharp2 installed, but I keep getting the following error message:

Probably you need the corresponding development package(s) as well?

See if installing 'libgtk2.0-dev' resolves the error.

---

### Post by kpkeerthi on 2009-08-19
[https://edge.launchpad.net/~banshee-unstable-team/+archive/ppa]("https://edge.launchpad.net/~banshee-unstable-team/+archive/ppa")

[https://edge.launchpad.net/~banshee-team/+archive/ppa]("https://edge.launchpad.net/~banshee-team/+archive/ppa")

---

