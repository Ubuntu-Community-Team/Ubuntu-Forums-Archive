---
title: "Make file doesn't work"
date: 2010-06-05
forum: General Help
---

### Post by mackay12 on 2010-06-05
Now before i get shouted at for not searching around i did, I have been through about 30 forum posts about the same problem, all the solutions did nothing for me, I have installed all packages those posts told me too but with no help. it still doesnt work. I just get this when I run "make"

```
make: *** No targets specified and no makefile found. Stop.
```

./configure worked and I have make files in the directory so i don't see why it isn't working, and Make is installed. along with build-essentials and others.

---

### Post by geirha on 2010-06-05
1. Did you read the README and/or INSTALL files bundled with the source (if any)
2. If this is a qt app, you might need to run qmake first to generate makefiles that make understands. If so, README/INSTALL should have instructions on that.
3. If the above didn't help, tell us what source you are trying to build, and/or show a listing of the files.

---

### Post by mackay12 on 2010-06-05
All the readme said was

```
 The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package, generally using the just-built uninstalled binaries.

  4. Type `make install' to install the programs and any data files and
     documentation.  When installing into a prefix owned by root, it is
     recommended that the package be configured and built as a regular
     user, and only the `make install' phase executed with root
     privileges.
```

I've had this problem with all Ubuntu versions I've used since 8.04

---

### Post by geirha on 2010-06-05
Then it doesn't sound like the configure script creates the Makefiles. Could you post the output of ./configure?

---

### Post by mackay12 on 2010-06-05
Well two makefiles WERE made, makefile.am and makefile.in

---

### Post by geirha on 2010-06-05
No, those aren't makefiles, they are used by automake and autoconf to generate the actual makefile. Is this source code checked out from a version control system, or did you download it as a tarball?

---

### Post by mackay12 on 2010-06-05
it was all in a .tar.gz which i extracted somewhere.

---

### Post by geirha on 2010-06-05
I see, well, the configure script typically creates makefiles out of Makefile.in, so it doesn't sounds like configure found all the needed dependencies.

---

### Post by mackay12 on 2010-06-05
so how can i fix this?

---

### Post by geirha on 2010-06-05
The output from configure will likely explain what it's missing...

---

### Post by mackay12 on 2010-06-05
Well this is what it produces, although its alot.

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking for gcc option to accept ISO C99... -std=gnu99
checking for gcc -std=gnu99 option to accept ISO Standard C... (cached) -std=gnu99
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
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
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for arpa/inet.h... yes
checking for arpa/nameser.h... yes
checking for fcntl.h... yes
checking for ifaddrs.h... yes
checking for netdb.h... yes
checking for netinet/in.h... yes
checking for sys/ioctl.h... yes
checking for sys/un.h... yes
checking for unistd.h... (cached) yes
checking for sys/socket.h... yes
checking for net/if.h... yes
checking for sys/types.h... (cached) yes
checking for netinet/in.h... (cached) yes
checking for arpa/nameser.h... (cached) yes
checking for netdb.h... (cached) yes
checking for resolv.h... yes
checking to see if compiler understands ... yes
checking to see if compiler understands -Wall... yes
checking to see if compiler understands -Wextra... yes
checking to see if compiler understands -Wdeclaration-after-statement... yes
checking to see if compiler understands -Wshadow... yes
checking to see if compiler understands -Wstrict-prototypes... yes
checking to see if compiler understands -Wmissing-declarations... yes
checking to see if compiler understands -Wmissing-prototypes... yes
checking to see if compiler understands -Wsign-compare... yes
checking to see if compiler understands -Wnested-externs... yes
checking to see if compiler understands -Wpointer-arith... yes
checking to see if compiler understands -Wformat-security... yes
checking to see if compiler understands -Winit-self... yes
checking to see if compiler understands -Werror... yes
checking to see if compiler understands -Wno-missing-field-initializers... yes
checking to see if compiler understands -Wno-error=missing-field-initializers... yes
checking to see if compiler understands -Wno-unused-parameter... yes
checking to see if compiler understands -Wno-error=unused-parameter... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GLIB... yes
checking for GMODULE... yes
checking for DBUS... no
configure: error: Package requirements (dbus-1 >= 1.1.0, dbus-glib-1 >= 0.82) were not met:

No package 'dbus-1' found
No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by geirha on 2010-06-05
There we have it, it doesn't find dbus-1 and dbus-glib-1.
Search for them with
```

aptitude search 'dbus.*-dev'

```
Make sure the two libs it needs is installed (has an **i** infront, and not a **p**); libdbus-1-dev and libdbus-glib-1-dev

---

### Post by mackay12 on 2010-06-05
thanks, i did a search in synaptic for those and i thought it said they were installed, guess i searched the wrong thing.

---

### Post by Leppie on 2010-06-05
are you compiling on a lucid system, or karmic?
try installing the newer dbus packages:
```
sudo apt-get install libdbus-1-3 libdbus-1-dev libdbus-glib-1-2
```

---

### Post by mackay12 on 2010-06-05
well um new problem,

```
Requested 'telepathy-glib >= 0.11.3' but version of Telepathy-GLib is 0.10.1
```

but I cannot find that version anywhere.

---

### Post by Leppie on 2010-06-05
what are you trying to install/compile?

---

### Post by mackay12 on 2010-06-05
telepathy-gabble is what I'm trying to install

---

### Post by Leppie on 2010-06-05
then why don't you install it from the repos?
```
sudo apt-get install telepathy-gabble
```

---

### Post by mackay12 on 2010-06-05
Because I never knew about it, every website told me to install it this way.

---

### Post by Leppie on 2010-06-05
ubuntu has very large repositories, if you want to install something you should first check them:
```
apt-cache search #keywords
```
in this case:
```
apt-cache search telepathy gabble
```
brings up:
```
telepathy-gabble - Jabber/XMPP connection manager
telepathy-gabble-dbg - Jabber/XMPP connection manager (debug symbols)
```

---

### Post by mackay12 on 2010-06-05
that doesnt work, it installs an older version, i need a newer version. that installed 0.8 when i need 0.9

---

### Post by geirha on 2010-06-05
You probably installed libdbus-1-3 and libdbus-glib-1-2, which you need installed to run a program that uses those libraries, but when you want to build something against a library, you need the corresponding -dev package for that library.

Now, as for the telepathy-glib dependency, you won't find a newer version in Ubuntu's repository (at least not until the next release), so you'll either have to find a ppa that has a newer version, or build it yourself from source.

---

### Post by Leppie on 2010-06-05
apparently that is a release available for maverick, you could try downloading it here: [http://launchpadlibrarian.net/48832298/telepathy-gabble_0.9.11-1_i386.deb](http://launchpadlibrarian.net/48832298/telepathy-gabble_0.9.11-1_i386.deb)

---

### Post by mackay12 on 2010-06-05
well I've made progress but now it says it needs sqlite3 so i installed it but it still says it.

---

### Post by Leppie on 2010-06-05
try installing the following packages:
```
sudo apt-get install libsqlite3-0 libsqlite3-dev
```

---

### Post by geirha on 2010-06-05
> **mackay12 said:**
> well I've made progress but now it says it needs sqlite3 so i installed it but it still says it.

libsqlite3-dev ?

---

### Post by Leppie on 2010-06-05
*

---

