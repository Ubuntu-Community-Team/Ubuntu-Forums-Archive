---
title: "How to install a program from source code?"
date: 2010-11-02
forum: General Help
---

### Post by boarder428 on 2010-11-02
I  am wonder if somebody could take the time to teach me to install or compile a program from source.  I have downloaded ZSNES from sourceforge but cannot figure out how to install it  from the command prompt or using the package manager.
Thanks in advance.
Corey

---

### Post by lisati on 2010-11-02
Does it include a "readme" file?

---

### Post by tajiknomi on 2010-11-02
[SIZE=2][I]I think when you downloaded it,it must be compressed,now extract it and look for the file name (**Install-sh**),...
open it(Run through terminal) and press Y for continuing installation.
[/I][/SIZE]

---

### Post by matt_symes on 2010-11-02
Hi

It very much depends on what language the application was written in. There is usually a readme file that will give instruction.

For c and c++, have the build-essentials package installed and there is generally a make file that you configure, build and then install.

Kind regards

---

### Post by katykat on 2010-11-02
Make sure you have compiler(s) installed. 

Typically commands are ./configure, make, make install 

But this may vary. 

Always read the docs, and if the commands are not found I would search synaptic for gcc and install related programs.

---

### Post by boarder428 on 2010-11-02
Thanks for all the responses!  I have reviewed the install read me file and am still having problems.
Here it is:> Linux/SDL/POSIX port:
I assume the standard development tools are installed (gcc, make, ...)
You'll also need :
- SDL (Simple DirectMedia Layer) : check [www.libsdl.org](www.libsdl.org) to grab SDL 1.2.0 or
                                   later. If you are using rpm packages, don't
                                   forget the -devel package.
- NASM v0.98.39 : [http://nasm.sf.net/](http://nasm.sf.net/)
- zlib v1.2.3 or higher : [http://www.zlib.net](http://www.zlib.net)
                                   it is probably already installed on your
                                   system, maybe you are just missing the
                                   development headers. Check in the
                                   packages available with your distribution
                                   or go to the page above
- libpng : [http://www.libpng.org/](http://www.libpng.org/)
                    You might also need libpng, ZSNES will compile without
                    PNG support but I have found doing so to make ZSNES
                    unstable for some weird reason.  If you don't have
                    libpng, either get it and install it or pass the
                    --without-png option to the 'configure' script.
- Curses/NCurses
             Check your distro. One of these is needed if you compile with
             the debugger enabled. You may also have to symlink ncurses.h
             to curses.h in your include directory.

Then to build the executable, go to the src directory and type:
sh ./autogen.sh && gmake && gmake install

Note: This only covers SVN/WIP builds, for releases see instructions below.

Note: autogen.sh requires automake and autoconf installed. Any parse errors
you recieve about configure.in are due to those not being installed.

Note: you require root to install zsnes to the the default (/usr/local/*)
directory

Also Note: libpng (optional) needs to be recent, or zsnes will not use it

You may also want to compress the zsnes executable with upx
([http://upx.sourceforge.net](http://upx.sourceforge.net)), it will divide its size by 10.



I am getting the following output when trying to compile:```
corey@corey-laptop ~/Downloads/zsnes_1_51/src $ gksudo sh ./autogen.sh && gmake && gmake install
Generating build information using aclocal and autoconf...
./autogen.sh: 6: sdl-config: not found
aclocal: couldn't open directory `/share/aclocal': No such file or directory
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
./configure: line 3542: syntax error near unexpected token `1.2.0,,AC_MSG_ERROR'
./configure: line 3542: `AM_PATH_SDL(1.2.0,,AC_MSG_ERROR(SDL >= 1.2.0 is required))'
No command 'gmake' found, did you mean:
 Command 'tmake' from package 'tmake' (universe)
 Command 'hmake' from package 'hmake' (universe)
 Command 'guake' from package 'guake' (universe)
 Command 'imake' from package 'xutils-dev' (main)
 Command 'mmake' from package 'mmake' (universe)
 Command 'omake' from package 'omake' (universe)
 Command 'jmake' from package 'dist' (universe)
 Command 'make' from package 'make' (main)
 Command 'dmake' from package 'dmake' (main)
 Command 'vmake' from package 'hdf4-tools' (universe)
 Command 'pmake' from package 'pmake' (main)
 Command 'qmake' from package 'qt4-qmake' (main)
 Command 'qmake' from package 'qt3-dev-tools' (main)
 Command 'cmake' from package 'cmake' (main)
gmake: command not found

```

I beleive that I installed all the files described in the read me text but seem to be having an issue.  I do not find a gmake package in synaptics.

---

### Post by matt_symes on 2010-11-02
Hi

gmake is the make file program just called make on Ubuntu.

In a terminal type 

alias gmake=make

and try to build again

Kind regards

---

### Post by SeijiSensei on 2010-11-02
Did you install build-essential first?

From the instructions it looks like you also need to install at least these packages:

libsdl1.2-dev
nasm
libpng12-dev

zlib is a quandry.  I think you probably want the zlibc package, but I don't know for sure.  

As for ncurses, it says this only applies to debugging, so you might want to disable it at compilation.  Run "./configure --help" in the source code directory to see a list of available options.  There may be a "--disable-ncurses" option you can try.

---

### Post by boarder428 on 2010-11-02
I made sure all the packages were installed and disabled the debugger and have an error at the end of the compile now.
```
corey@corey-laptop ~/Downloads/zsnes_1_51/src $ gksudo sh ./autogen.sh && make && make install
Generating build information using aclocal and autoconf...
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... yes
checking for initscr in -lncurses... yes
checking for initscr in -lpdcurses... no
checking if you want libao support... no
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for glGetError in -lGL... yes
checking for OpenGL... yes
checking for JMA support... yes
checking for cpu info... failed
checking if you want gdb friendly executable... no
checking which cpu architecture to optimize for... guessing i386
checking if you want crazy optimizations... no
checking for grep that handles long lines and -e... configure: WARNING: This is not what you want, use --target or force-arch
/bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... no
checking for sys/types.h... no
checking for sys/stat.h... no
checking for stdlib.h... no
checking for string.h... no
checking for memory.h... no
checking for strings.h... no
checking for inttypes.h... no
checking for stdint.h... no
checking for unistd.h... no
checking whether sys/types.h defines makedev... no
checking sys/mkdev.h usability... no
checking sys/mkdev.h presence... no
checking for sys/mkdev.h... no
checking sys/sysmacros.h usability... no
checking sys/sysmacros.h presence... yes
configure: WARNING: sys/sysmacros.h: present but cannot be compiled
configure: WARNING: sys/sysmacros.h:     check for missing prerequisite headers?
configure: WARNING: sys/sysmacros.h: see the Autoconf documentation
configure: WARNING: sys/sysmacros.h:     section "Present But Cannot Be Compiled"
configure: WARNING: sys/sysmacros.h: proceeding with the compiler's result
checking for sys/sysmacros.h... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h


ZSNES v1.51

SDL support                   Version 1.2.14
NASM support                  NASM version 2.07 compiled on Nov  5 2009
zlib support                  Version 1.2.3.3
PNG support                   Yes, version 1.2.42
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled

The binary will be installed in /usr/local/bin

Configure complete, now type 'make' and pray.

g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=i386 -O3 -fomit-frame-pointer -s -fno-rtti -o tools/fileutil.o -c tools/fileutil.cpp
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
make: *** [tools/fileutil.o] Error 1
corey@corey-laptop ~/Downloads/zsnes_1_51/src $ make
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__OPENGL__ -march=i386 -O3 -fomit-frame-pointer -s -fno-rtti -o tools/fileutil.o -c tools/fileutil.cpp
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
tools/fileutil.cpp:1: error: CPU you selected does not support x86-64 instruction set
make: *** [tools/fileutil.o] Error 1
corey@corey-laptop ~/Downloads/zsnes_1_51/src $ make:
No command 'make:' found, did you mean:
 Command 'makeg' from package 'xutils-dev' (main)
 Command 'make' from package 'make' (main)
make:: command not found

```

---

### Post by mc4man on 2010-11-03
zsnes is really meant to be built/run on a 32 bit install, building and having that  build, even if successful, run right on a_64 install is difficult at best.

What you may want to try is this ppa and see if it works out.
[https://launchpad.net/~smaxein/+archive/ppa/+packages](https://launchpad.net/~smaxein/+archive/ppa/+packages)

The other option would be to add ia32-libs, maybe a few add. libs with getlibs and install the 32 bit version.
(possibly libsdl-image1.2 - I have a couple of 32 bit installs already so many 32 bit libs are already in place ) 
I got it (a 32 bit ver.), installed/running on a mav 64 bit, but nothing to test with - (it opened fine, all the menus were accessible, could alter the rez, ect.

I'd try that ppa...

---

### Post by matt_symes on 2010-11-03
Hi

Also, in future, type

make

and not 

make:

Kind regards

---

### Post by boarder428 on 2010-11-03
Thanks mc4man, I was wondering if that may be an issue.  I'm still green when it comes to compiling, I did'nt quite understand what the compiler was telling me.  I may try to compile it some other pc's I have that run 32 bit.  I've keep forgetting the issues with 64 bit distros, I've always run them on my AMD machines.  I'll probably go back to 32 bit next upgrade.
Corey

---

### Post by mc4man on 2010-11-03
> I may try to compile it some other pc's I have that run 32 bit
Overall it's probably still going to fail if you use the source it appeared you were using.
It would likely need some minor patching for debian/ubuntu.
For info purposes, because it's available in ubuntu repo's you could - 
apt-get source zsnes
Take a look in the /debian/patches folder (1_51b.dpatch) if you get any compiler errors, probably from some missing defines
Most of what's in the dpatch may already be included but, as mentioned, some defines may be missing.
(also run sudo apt-get build-dep zsnes to fill in any missing deps

From a clean(ed) source -  cd to src and run 
autoreconfig

Then a ./configure as or similar to below - taken from the  /debian/rules file 
(may present  a more 'suitable' configure - otherwise you may get a successful build that segfaults when run.
```
CFLAGS="-U_FORTIFY_SOURCE" ./configure --enable-opengl --disable-cpucheck \
--enable-release --disable-debugger --enable-libao force_arch=i486

```
Should prove to be an 'interesting build', though you could just as well install from repo. (I'd do the build just because.., if your build doesn't work out use the repo version. The source won't create a menu item - you'll need to create one
You can install with sudo make install or 
```
sudo checkinstall --pkgname zsnes --pkgversion 1.5.1 --backup=no \
--default --deldoc=yes --deldesc=yes --delspec=yes --fstrans=no

```

Edit:
forgot to mention - a possible configure for 64 bit - assuming you have ia32-libs and some add. links (look in the /debian/rules for clue - as mentioned here had all already w/  [getlibs]("http://ubuntuforums.org/showthread.php?t=474790") 

```
CFLAGS="-m32 -U_FORTIFY_SOURCE" ./configure --enable-opengl --disable-cpucheck \
--enable-release --disable-debugger --enable-libao force_arch=i486
```

---

### Post by boarder428 on 2010-11-04
thanks mc4man, it may be over my head, I'm still very new to linux and compiling from source.  If I can't find it in synaptics or software manager I'm pretty much lost.  I figured since that was the case maybey it was time for me to learn to compile from source.  I did'nt realize there was that much to it.  I kinda thought it was the norm for Linux.  I could probably waste everyones time for days trying to figure this out. I have other pc's running 32 bit installs, at my skill level it's probably better for me to try it on one of them.

---

### Post by boarder428 on 2010-11-06
> **mc4man said:**
> zsnes is really meant to be built/run on a 32 bit install, building and having that  build, even if successful, run right on a_64 install is difficult at best.

What you may want to try is this ppa and see if it works out.
[https://launchpad.net/~smaxein/+archive/ppa/+packages](https://launchpad.net/~smaxein/+archive/ppa/+packages)

I tried the ppa and it did not seem to work. It started to run and closed.

---

