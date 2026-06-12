---
title: "gerd.tar.gz"
date: 2009-09-14
forum: General Help
---

### Post by asbloodrunsblack on 2009-09-14
i have tried many times to get this to install and i cant find any other version of the file to make it easier...

kris@kris-laptop:~$ tar xvf gerd-0.0.3.tar.gz
tar: gerd-0.0.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
kris@kris-laptop:~$ 



the file is on my desktop.

---

### Post by kogger on 2009-09-14
You're in the wrong folder. The file is on your desktop, but your terminal is in your home folder. Use 'cd Desktop', and then re-do your commands.

---

### Post by sunchiqua on 2009-09-14
If it's on your desktop:

```
cd $HOME/Desktop
tar xvf gerd-0.0.3.tar.gz
```

---

### Post by jocko on 2009-09-14
> **asbloodrunsblack said:**
> i have tried many times to get this to install and i cant find any other version of the file to make it easier...

kris@kris-laptop:~$ tar xvf gerd-0.0.3.tar.[COLOR=Red]gz[/COLOR]
tar: gerd-0.0.3.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
kris@kris-laptop:~$ 



[COLOR=Red]the file is on my desktop[/COLOR].
If the file is on your desktop:
```
cd ~/Desktop
```
And if the file is a .tar.gz, you need to pass a it through gzip, so add a "z" to the options:
```
tar -xv[COLOR=Red]z[/COLOR]f gerd-0.0.3.tar.gz
```

---

### Post by asbloodrunsblack on 2009-09-14
did this.. now what? and tyvm

---

### Post by sunchiqua on 2009-09-14
> **asbloodrunsblack said:**
> did this.. now what? and tyvm

Standard procedure ( don't forget to be in the right directory ):

```

./configure
make
sudo make install
```

---

### Post by asbloodrunsblack on 2009-09-14
kris@kris-laptop:~/Desktop$ gerd-0.0.3/configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... yes
checking whether gcc accepts -g... yes
checking how to run the C preprocessor... gcc -E
checking for working const... yes
checking whether gcc needs -traditional... no
checking for inline... inline
checking for ANSI C header files... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking for ranlib... ranlib
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD-compatible nm... /usr/bin/nm -B
updating cache ./config.cache
loading cache ./config.cache within ltconfig
checking for object suffix... o
checking for executable suffix... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... no
checking if we can lock with hard links... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... ok
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for objdir... .libs
creating libtool
updating cache ./config.cache
loading cache ./config.cache
checking for X... no
checking for gtk-config... no
checking for GTK - version >= 1.2.7... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find GTK gtk-config missing from path?
kris@kris-laptop:~/Desktop$

---

### Post by asbloodrunsblack on 2009-09-14
guess no one has a response to this one?

---

### Post by NoaHall on 2009-09-14
sudo apt-get install xserver-xorg-dev

---

### Post by asbloodrunsblack on 2009-09-14
did that
says same thing

---

### Post by NoaHall on 2009-09-14
sudo apt-get install gtkgl-dev 

I can't remember the name of the package you need, but if you check the read me, it should say what you need.

---

### Post by asbloodrunsblack on 2009-09-14
i figured that part out on my own..

now i get yet again.. another error when i try and make install

kris@kris-laptop:~/Desktop$ gerd-0.0.3/configure
loading cache ./config.cache
checking for a BSD compatible install... (cached) /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... (cached) yes
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking whether to enable maintainer-specific portions of Makefiles... no
checking host system type... i686-pc-linux-gnu
checking for gcc... (cached) gcc
checking whether the C compiler (gcc  ) works... yes
checking whether the C compiler (gcc  ) is a cross-compiler... no
checking whether we are using GNU C... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking how to run the C preprocessor... (cached) gcc -E
checking for working const... (cached) yes
checking whether gcc needs -traditional... (cached) no
checking for inline... (cached) inline
checking for ANSI C header files... (cached) yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln -s works... (cached) yes
checking build system type... i686-pc-linux-gnu
checking for ranlib... (cached) ranlib
checking for ld used by GCC... (cached) /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... (cached) yes
checking for BSD-compatible nm... (cached) /usr/bin/nm -B
loading cache ./config.cache within ltconfig
checking for object suffix... o
checking for executable suffix... (cached) no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... no
checking if we can lock with hard links... yes
checking if gcc supports -fno-rtti -fno-exceptions ... no
checking if gcc static flag -static works... -static
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the linker (/usr/bin/ld) supports shared libraries... yes
checking command to parse /usr/bin/nm -B output... ok
checking how to hardcode library paths into programs... immediate
checking for /usr/bin/ld option to reload object files... -r
checking dynamic linker characteristics... Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for objdir... .libs
creating libtool
loading cache ./config.cache
checking for X... no
checking for gtk-config... /usr/bin/gtk-config
checking for GTK - version >= 1.2.7... yes
checking for putenv... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking for fcntl.h... yes
checking for sys/ioctl.h... yes
checking for unistd.h... yes
checking for waitpid... yes
checking for putenv... (cached) yes
checking return type of signal handlers... void
checking for compatible Gtk+ version... 1.2.10 works fine
updating cache ./config.cache
creating ./config.status
creating Makefile
creating gerd/Makefile
creating gerd/gerdconfig.h
creating config.h
kris@kris-laptop:~/Desktop$ sudo make install
Making install in gerd
make[1]: Entering directory `/home/kris/Desktop/gerd'
/bin/sh ../libtool --mode=compile gcc -DG_LOG_DOMAIN=\"Gerd\" -I../gerd-0.0.3 -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DGTK_DISABLE_COMPAT_H    -g -Wall -Wshadow -Wmissing-prototypes -Wmissing-declarations -Winline -Wpointer-arith -Wcast-align -O6 -pipe -fstrength-reduce -fexpensive-optimizations -finline-functions -frerun-cse-after-loop -freg-struct-return -fnonnull-objects -c ../gerd-0.0.3/gerd/gerd-utils.c
gcc -DG_LOG_DOMAIN=\"Gerd\" -I../gerd-0.0.3 -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DGTK_DISABLE_COMPAT_H -g -Wall -Wshadow -Wmissing-prototypes -Wmissing-declarations -Winline -Wpointer-arith -Wcast-align -O6 -pipe -fstrength-reduce -fexpensive-optimizations -finline-functions -frerun-cse-after-loop -freg-struct-return -fnonnull-objects -c  -fPIC -DPIC ../gerd-0.0.3/gerd/gerd-utils.c
cc1: warning: command line option "-fnonnull-objects" is valid for C++/ObjC++ but not for C
../gerd-0.0.3/gerd/gerd-utils.c: In function 'gerd_widget_add_window':
../gerd-0.0.3/gerd/gerd-utils.c:173: error: expected ')' before '__PRETTY_FUNCTION__'
make[1]: *** [gerd-utils.lo] Error 1
make[1]: Leaving directory `/home/kris/Desktop/gerd'
make: *** [install-recursive] Error 1
kris@kris-laptop:~/Desktop$ make
make  all-recursive
make[1]: Entering directory `/home/kris/Desktop'
Making all in gerd
make[2]: Entering directory `/home/kris/Desktop/gerd'
/bin/sh ../libtool --mode=compile gcc -DG_LOG_DOMAIN=\"Gerd\" -I../gerd-0.0.3 -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DGTK_DISABLE_COMPAT_H    -g -Wall -Wshadow -Wmissing-prototypes -Wmissing-declarations -Winline -Wpointer-arith -Wcast-align -O6 -pipe -fstrength-reduce -fexpensive-optimizations -finline-functions -frerun-cse-after-loop -freg-struct-return -fnonnull-objects -c ../gerd-0.0.3/gerd/gerd-utils.c
gcc -DG_LOG_DOMAIN=\"Gerd\" -I../gerd-0.0.3 -I.. -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -DGTK_DISABLE_COMPAT_H -g -Wall -Wshadow -Wmissing-prototypes -Wmissing-declarations -Winline -Wpointer-arith -Wcast-align -O6 -pipe -fstrength-reduce -fexpensive-optimizations -finline-functions -frerun-cse-after-loop -freg-struct-return -fnonnull-objects -c  -fPIC -DPIC ../gerd-0.0.3/gerd/gerd-utils.c
cc1: warning: command line option "-fnonnull-objects" is valid for C++/ObjC++ but not for C
../gerd-0.0.3/gerd/gerd-utils.c: In function 'gerd_widget_add_window':
../gerd-0.0.3/gerd/gerd-utils.c:173: error: expected ')' before '__PRETTY_FUNCTION__'
make[2]: *** [gerd-utils.lo] Error 1
make[2]: Leaving directory `/home/kris/Desktop/gerd'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kris/Desktop'
make: *** [all-recursive-am] Error 2

---

### Post by NoaHall on 2009-09-14
It looks like bad coding to me. What application is this?

You could also try install a different version of gcc ++, it might help

---

### Post by asbloodrunsblack on 2009-09-14
it was a cursor recording and playback tool.. if you can find a better one i'll gladly use

---

### Post by NoaHall on 2009-09-14
Try this - [http://ikester.blogspot.com/2007/01/im-huge-fan-of-autohotkey.html](http://ikester.blogspot.com/2007/01/im-huge-fan-of-autohotkey.html)

I haven't tested it, but apparently it's in synaptic. No messing around with code.

Have you got a link to that program's site?

---

### Post by jocko on 2009-09-14
> **asbloodrunsblack said:**
> ...
checking for [COLOR=Red]gtk-config[/COLOR]... no
checking for [COLOR=Red]GTK[/COLOR] - version >= 1.2.7... no
*** The [COLOR=Red]gtk-config[/COLOR] script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
[COLOR=Red]configure: error: Cannot find GTK gtk-config missing from path?[/COLOR]

Did you install libgtk2.0-dev?
Edit: I was a little bit slow with my typing, so you seem to have solved that part already...

---

### Post by asbloodrunsblack on 2009-09-14
[http://testbit.eu/~timj/historic/gerd/]("http://testbit.eu/%7Etimj/historic/gerd/")
and yes i installed

---

### Post by luigi_mb on 2009-09-14
[QUOTE=asbloodrunsblack;7948118]kris@kris-laptop:~/Desktop$ 
gerd-0.0.3/configure
...

Try this

```

$ cd Desktop/gerd-0.0.3
./configure 
...

```

---

