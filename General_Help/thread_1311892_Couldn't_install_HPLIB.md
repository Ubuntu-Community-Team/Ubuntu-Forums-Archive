---
title: "Couldn't install HPLIB"
date: 2009-11-02
forum: General Help
---

### Post by jhb1608 on 2009-11-02
I tried to install from HP's directions, but the specific file "configure: error: "cannot find libjpeg support" won't load.

```
jason@jason-desktop:~$ cd Desktop
jason@jason-desktop:~/Desktop$ ls
hplip-3.9.8  hplip-3.9.8.tar.gz  My Budget.ods
jason@jason-desktop:~/Desktop$ cd hplip-3.9.8
jason@jason-desktop:~/Desktop/hplip-3.9.8$ make
make: *** No targets specified and no makefile found.  Stop.
jason@jason-desktop:~/Desktop/hplip-3.9.8$ ./configure --with-hpppddir=/usr/share/ppd/HP --prefix=/usr --enable-qt4 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --disable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether we are using the GNU C++ compiler... (cached) no
checking whether g++ accepts -g... (cached) no
checking dependency style of g++... (cached) none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for pthread_create in -lpthread... yes
checking for pow in -lm... yes
checking for jpeg_set_defaults in -ljpeg... no
configure: error: "cannot find libjpeg support"
```

I use Ubuntu 9.10, by the way. I don't understand.

---

### Post by Giblet5 on 2009-11-02
The package relies on the jpeg development libraries.

```
sudo apt-get install libjpeg62-dev
```

will fix that missing library. There will probably be others. Just search Synaptic for the missing library name and select the xxxxxxx-dev version of it.

---

### Post by jhb1608 on 2009-11-02
wow more errors.

```
jason@jason-desktop:~$ cd Desktop
jason@jason-desktop:~/Desktop$ cd hplip-3.9.8
jason@jason-desktop:~/Desktop/hplip-3.9.8$ make
make: *** No targets specified and no makefile found.  Stop.
jason@jason-desktop:~/Desktop/hplip-3.9.8$ ./configure --with-hpppddir=/usr/share/ppd/HP --prefix=/usr --enable-qt4 --enable-doc-build --disable-cups-ppd-install --disable-foomatic-drv-install --disable-foomatic-ppd-install --disable-hpijs-install --disable-policykit --enable-cups-drv-install --enable-hpcups-install --enable-network-build --enable-dbus-build --enable-scan-build --enable-fax-build
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether we are using the GNU C++ compiler... (cached) no
checking whether g++ accepts -g... (cached) no
checking dependency style of g++... (cached) none
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking for pthread_create in -lpthread... yes
checking for pow in -lm... yes
checking for jpeg_set_defaults in -ljpeg... yes
checking for dlopen in -ldl... yes
checking pthread.h usability... yes
checking pthread.h presence... yes
checking for pthread.h... yes
checking jpeglib.h usability... yes
checking jpeglib.h presence... yes
checking for jpeglib.h... yes
checking whether byte ordering is bigendian... no
checking for uint32_t... yes
checking "for platform-dependencies"... "using Default platform.h"
checking for documentation build... yes
checking for hpijs only build... no
checking for lite build... no
checking for hpijs install... no
checking for hpcups install... yes
checking for new hpcups install... no
checking for network build... yes
checking for parallel port build... no
checking for scanner build... yes
checking for gui build... yes
checking for fax build... yes
checking for dbus build... yes
checking for cups 1.1.x build... no
checking for udev acl rules... no
checking for shadow build... no
checking for foomatic ppd install... no
checking for foomatic drv install... no
checking for cups drv install... yes
checking for cups ppd install... no
checking for foomatic-rip-hplip install... no
checking for qt4... yes
checking for qt3... no
checking for policykit... no
checking for host machine platform... x86_32
checking for CRYPTO_free in -lcrypto... no
configure: error: cannot find net-snmp support (or --disable-network-build)
```

Weird.

---

### Post by ea1387 on 2009-11-02
Actually HPLIP should be already installed on your system, it is preinstall on Ubuntu, check your synaptic manager and do a search for hplip and you should see the package.

---

### Post by Giblet5 on 2009-11-02
> **ea1387 said:**
> Actually HPLIP should be already installed on your system, it is preinstall on Ubuntu, check your synaptic manager and do a search for hplip and you should see the package.

Yeah sure, if ya want the EASY way out... :)

---

### Post by jhb1608 on 2009-11-02
got it working! odd. hplib package works out of ubuntu's software program. So strange though.

---

### Post by ea1387 on 2009-11-02
Yea i had to buy a HP Printer because my Kodak didn't support Linux, and checked everything on the HPLIP website and it told me that the latest package of hplip should be preinstalled on my system and i checked and it was.

---

