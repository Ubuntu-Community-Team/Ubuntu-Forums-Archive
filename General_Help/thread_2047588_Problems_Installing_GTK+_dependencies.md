---
title: "Problems Installing GTK+ dependencies"
date: 2012-08-25
forum: General Help
---

### Post by che47audio on 2012-08-25
Hi,

This is my first attempt at compiling source code to make an install, and I'm falling at the first hurdle. I've downloaded the latest source code from the GTK website, extracted it in my Downloads folder, cd'd into this folder in the terminal and ran ```
./configure
``` and I'm getting the following output...


```

chris@kestrel:~$ cd Downloads/gtk+-3.4.4/
chris@kestrel:~/Downloads/gtk+-3.4.4$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
checking whether make supports nested variables... yes
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
checking whether gcc and cc understand -c and -o together... yes
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking whether make sets $(MAKE)... (cached) yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for native Win32... no
checking for c++... c++
checking whether we are using the GNU C++ compiler... yes
checking whether c++ accepts -g... yes
checking dependency style of c++... gcc3
checking how to print strings... printf
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking how to convert x86_64-unknown-linux-gnu file names to x86_64-unknown-linux-gnu format... func_convert_file_noop
checking how to convert x86_64-unknown-linux-gnu file names to toolchain format... func_convert_file_noop
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for dlltool... no
checking how to associate runtime and link libraries... printf %s\n
checking for ar... ar
checking for archiver @FILE support... @
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
checking how to run the C preprocessor... gcc -std=gnu99 -E
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
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking how to run the C++ preprocessor... c++ -E
checking for ld used by c++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the c++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for c++ option to produce PIC... -fPIC -DPIC
checking if c++ PIC flag -fPIC -DPIC works... yes
checking if c++ static flag -static works... yes
checking if c++ supports -c -o file.o... yes
checking if c++ supports -c -o file.o... (cached) yes
checking whether the c++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... (cached) GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
configure: creating ./config.lt
config.lt: creating libtool
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking dependency style of gcc -std=gnu99... gcc3
checking for nm... /usr/bin/nm -B
checking for some Win32 platform... no
checking whether build environment is sane... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for BASE_DEPENDENCIES... no
configure: error: Package requirements (glib-2.0 >= 2.32.0    atk >= 2.2.0    pango >= 1.30.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.26.0) were not met:

No package 'atk' found
No package 'pango' found
No package 'cairo' found
No package 'cairo-gobject' found
No package 'gdk-pixbuf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
chris@kestrel:~/Downloads/gtk+-3.4.4$ 
```


How do I install the packages that it hasn't found? Is there a way to install all GTK+ build dependencies in one swoop? Any help much appreciated.

Cheers
Chris

---

### Post by Rexilion on 2012-08-25
For the packages you mentioned:

```
aptitude -R install libatk1.0-dev libpango1.0-dev libcairo2-dev libcairo-gobject2 libgdk-pixbuf2.0-dev
```

But an 'automatic' way is to use:

```
aptitude -R build-dep libgtk-3-0 libgtk-3-bin libgtk-3-common
```

Altough this might pull in way more dev-packages than you might need!

Have fun compiling and dep hunting! :popcorn:

---

### Post by MiraMaX166 on 2012-10-05
Big thanks!!!:)

---

