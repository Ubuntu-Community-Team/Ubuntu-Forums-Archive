---
title: "I need help installing this tar.gz file"
date: 2011-12-27
forum: General Help
---

### Post by TheNerdAL on 2011-12-27
Trying to install Unico for a theme, but it's a tar.gz file and I ALWAYS never successfully install those. :(

Can anyone help me? 

[https://launchpad.net/unico](https://launchpad.net/unico)

Thanks!

---

### Post by zero2xiii on 2011-12-27
Hay,

Usually the generic instructions is as follows:
extract archive
open terminal and cd to archive extraction location
execute **./configure**
execute **make**
execute **make install**
Program should now be installed.

If however you get a failed configure step, please post the output of the terminal so we can see what the problems is, and maybe help you fix them.

Cherz

---

### Post by Schugy on 2011-12-27
This is the [askubuntu solution]("http://askubuntu.com/questions/28372/how-do-i-get-the-source-code-of-packages-installed-through-apt-get").

---

### Post by TheNerdAL on 2011-12-27
> **zero2xiii said:**
> Hay,

Usually the generic instructions is as follows:
extract archive
open terminal and cd to archive extraction location
execute **./configure**
execute **make**
execute **make install**
Program should now be installed.

If however you get a failed configure step, please post the output of the terminal so we can see what the problems is, and maybe help you fix them.

Cherz

When I do the **make** it gives me this: 

```
make: *** No targets specified and no makefile found.  Stop.
```

---

### Post by TheNerdAL on 2011-12-27
need help. :(

---

### Post by WorMzy on 2011-12-27
That suggests that you're either a) not in the correct directory, b) haven't run configure yet, or c) have run configure, but it failed to execute correctly.


So, make sure you're in the correct directory, make sure to run ./configure, and if you get any errors, post them here.

---

### Post by TheNerdAL on 2011-12-27
> **WorMzy said:**
> That suggests that you're either a) not in the correct directory, b) haven't run configure yet, or c) have run configure, but it failed to execute correctly.


So, make sure you're in the correct directory, make sure to run ./configure, and if you get any errors, post them here.

I went in the downloads folder by doing "cd Downloads" Then went into the folder itself "cd foldername" 

then I did ./configure, then it seemed like it worked since I saw a list of stuff.

---

### Post by WorMzy on 2011-12-27
Well, I downloaded the source and compiled it without issue, so I have to assume something went wrong on your end. Without more information, I couldn't begin to guess at what that might be. ;)

---

### Post by TheNerdAL on 2011-12-27
> **WorMzy said:**
> Well, I downloaded the source and compiled it without issue, so I have to assume something went wrong on your end. Without more information, I couldn't begin to guess at what that might be. ;)

Can you give me instructions on how to do it? :(

---

### Post by WorMzy on 2011-12-27
The instructions are the ones you seem to be following.

```
./configure
make
make install
```

That's all.


If it's going wrong for you, then we need to see the output for the ./configure step.

---

### Post by TheNerdAL on 2011-12-27
Here's the ./configure part: 

```
adrian@UbuntuComputer:~/Desktop/unico-1.0.1$ ./configure
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
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking how to print strings... printf
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
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for sysroot... no
checking for mt... mt
checking if mt is a manifest tool... no
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
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for glib-mkenums... no
checking for glib-genmarshal... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... no
configure: error: Package requirements (glib-2.0 >= 2.26.0 gtk+-3.0 >= 3.1.10 cairo >= 1.10) were not met:

No package 'glib-2.0' found
No package 'gtk+-3.0' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
adrian@UbuntuComputer:~/Desktop/unico-1.0.1$ make
make: *** No targets specified and no makefile found.  Stop.
adrian@UbuntuComputer:~/Desktop/unico-1.0.1$ 

```

---

### Post by oldos2er on 2011-12-27
Why not make use the *deb file? [https://launchpad.net/ubuntu/+source/gtk3-engines-unico](https://launchpad.net/ubuntu/+source/gtk3-engines-unico)

---

### Post by TheNerdAL on 2011-12-27
> **oldos2er said:**
> Why not make use the *deb file? [https://launchpad.net/ubuntu/+source/gtk3-engines-unico](https://launchpad.net/ubuntu/+source/gtk3-engines-unico)

Where's the deb file at? O.o

---

### Post by WorMzy on 2011-12-27
*sigh*

You see that error message part of the ./configure output? The bit about unmet package requirements? That's what we in the compilation business call a "hint". :P

Install glib-2.0, gtk+-3.0, cairo, and their -dev packages. I believe that the following command will take care of that for you, although, thanks to Ubuntu/Debian's bizarre naming and trigger happy package splitting, I can't guarantee that it will.

```
sudo apt-get install libglib2.0-0 libglib2.0-dev libgtk-3-0 libgtk-3-dev libcairo2 libcairo2-dev
```

Then try the ./configure command again.

---

### Post by TheNerdAL on 2011-12-27
I think it didn't work: 

```
adrian@UbuntuComputer:~/Desktop/unico-1.0.1$ make install
Making install in build
make[1]: Entering directory `/home/adrian/Desktop/unico-1.0.1/build'
make[2]: Entering directory `/home/adrian/Desktop/unico-1.0.1/build'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/build'
make[1]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/build'
Making install in unico
make[1]: Entering directory `/home/adrian/Desktop/unico-1.0.1/unico'
make[2]: Entering directory `/home/adrian/Desktop/unico-1.0.1/unico'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gtk-3.0/3.0.0/theming-engines" || /bin/mkdir -p "/usr/local/lib/gtk-3.0/3.0.0/theming-engines"
/bin/mkdir: cannot create directory `/usr/local/lib/gtk-3.0': Permission denied
make[2]: *** [install-engineLTLIBRARIES] Error 1
make[2]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/unico'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/unico'
make: *** [install-recursive] Error 1

```

---

### Post by WorMzy on 2011-12-27
Now what you have is a permissions error, due to your user not having write permissions to the intended destination folder.

Solution:

```
sudo make install
```

Don't be afraid to read the output yourself -- despite what it might look like at first glance, it's not actually in a foreign language. ;)

---

### Post by TheNerdAL on 2011-12-27
Did I do it right?! :D 

```
sudo make install
[sudo] password for adrian: 
Making install in build
make[1]: Entering directory `/home/adrian/Desktop/unico-1.0.1/build'
make[2]: Entering directory `/home/adrian/Desktop/unico-1.0.1/build'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/build'
make[1]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/build'
Making install in unico
make[1]: Entering directory `/home/adrian/Desktop/unico-1.0.1/unico'
make[2]: Entering directory `/home/adrian/Desktop/unico-1.0.1/unico'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/gtk-3.0/3.0.0/theming-engines" || /bin/mkdir -p "/usr/local/lib/gtk-3.0/3.0.0/theming-engines"
 /bin/bash ../libtool   --mode=install /usr/bin/install -c   libunico.la '/usr/local/lib/gtk-3.0/3.0.0/theming-engines'
libtool: install: /usr/bin/install -c .libs/libunico.so /usr/local/lib/gtk-3.0/3.0.0/theming-engines/libunico.so
libtool: install: /usr/bin/install -c .libs/libunico.lai /usr/local/lib/gtk-3.0/3.0.0/theming-engines/libunico.la
libtool: install: /usr/bin/install -c .libs/libunico.a /usr/local/lib/gtk-3.0/3.0.0/theming-engines/libunico.a
libtool: install: chmod 644 /usr/local/lib/gtk-3.0/3.0.0/theming-engines/libunico.a
libtool: install: ranlib /usr/local/lib/gtk-3.0/3.0.0/theming-engines/libunico.a
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/sbin" ldconfig -n /usr/local/lib/gtk-3.0/3.0.0/theming-engines
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib/gtk-3.0/3.0.0/theming-engines

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
make[2]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/unico'
make[1]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/unico'
Making install in tests
make[1]: Entering directory `/home/adrian/Desktop/unico-1.0.1/tests'
make[2]: Entering directory `/home/adrian/Desktop/unico-1.0.1/tests'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/tests'
make[1]: Leaving directory `/home/adrian/Desktop/unico-1.0.1/tests'
make[1]: Entering directory `/home/adrian/Desktop/unico-1.0.1'
make[2]: Entering directory `/home/adrian/Desktop/unico-1.0.1'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/adrian/Desktop/unico-1.0.1'
make[1]: Leaving directory `/home/adrian/Desktop/unico-1.0.1'
adrian@UbuntuComputer:~/Desktop/unico-1.0.1$ 

```

EDIT: I think I did it right.

---

### Post by *nixgirl on 2011-12-27
Are you using an older version of ubuntu (since gtk is normally included in the package)?

First make sure you have glib-2.0, gtk+-3.0 and cairo installed (apt-get install these with any dependencies that they may require).

Only then do the "make" and "make configure".

As regards the theme directory structure, it should be:
~/.themes/themename/gtk-2.0/
(with .gtkrc sitting inside the gtk-2.0 dir)
(or, in my case /I'm using openbox/, it is:  
~/.themes/themename/openbox).

---

### Post by WorMzy on 2011-12-27
Looks like it to me. 'grats. :D

---

### Post by TheNerdAL on 2011-12-27
Thanks! I'm learning how to use Terminal! 

And no, I am using 11.10.

---

### Post by oldos2er on 2011-12-27
> **TheNerdAL said:**
> Where's the deb file at? O.o

At the URL I gave, click the triangle under 'The Oneiric Ocelot.' But I see you have the source code installed.

---

