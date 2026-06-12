---
title: "alot of System problems"
date: 2006-05-29
forum: General Help
---

### Post by 2pacalypse on 2006-05-29
I recently got some rather annoying problems in my computer, i know that these problem's are not really Ubuntu based (except the Synaptic Package Manager) but when I ran simular things in Knoppix/OpenSuSE or WinXP(A.K.A. the curesed system) I didnt had these problems so these problem's are only in the Ubuntu system

1-All my browser's Keep crashing at random occasions, i'm just scrolling down the page and then bam, im back in my Desktop, no error message no log, simply nothing. and this happends repeatdly. please help

2-My Pages/Notes/Games (pretty much anything which uses the scrool on the mouse) is constantly moving up and down fast like some1 is playing around with the mouse wheel evev When no body is even touching the wheel and no one is even near the computer.

3-I installed some stuff with my Synaptic Package Manager, but altough its installed, 80 precent of it is no where to be seen on the system. altought the Synapic Package Manager claims that its installed. I even tried to reinstall it but no luck. among the things are - Nethack (the RPG) Arkhart (MMORPG) Aegis Virus Scanner Scorched 3D (Game), Stargus (another game), Freecraft (another game). there are many more programs/games like that which were install in the Synaptic Package Manager but are not in the system. how do I run them?

4-I dont have sound in my games. I have sound in my Mp3 players, and in my OS but not in games. 

5-The Game Battle for Wesnoth doesnt have sound and also crash's very frequntly. When i played that game in SuSE 10.1 he ran rather well (with rare crash's) with full sound and everything, what wrong with it in Ubuntu?

6-half of the applications that were installed in the system via Synaptic Package Manager were badly installed. when ever i run it the screen flash's (like its beginning to run them) but then i just return to my Desktop.

7-My Azureus keeps disappearing. i go for a minute to have a drink or something like that and when im back Azureus isnt running anymore

8)When im compiling a program (in this case kguitar but this error also happend in other programs) he cant finish the ./configure stage, hen ever i do it he gives me

```

yaniv@2pacalypse:~/Desktop/Kguitar/kguitar-0.5$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
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
checking how to run the C preprocessor... gcc -E
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
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wnon-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
checking whether g++ supports -O0... no
checking whether g++ supports --Wl,--warn-unresolved-symbols... no
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking for g77... g77
checking whether we are using the GNU Fortran 77 compiler... yes
checking whether g77 accepts -g... yes
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
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
libtool.m4: error: problem compiling CXX test program
checking for g++ option to produce PIC...
checking if g++ supports -c -o file.o... no
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking if C++ programs can be compiled... no
configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similiar to libstd++-dev.

```

when ever i look in the Synaptic Package Manager for this libstd++-dev i cant find it all i can find is libstdc++<version>-dev/dbg/glibc and other stuff like that (sometimes its just blank). i installed all those libstdc++ lib files but i still get this error during compilation. what should i do?

9-When i run GuitarPro 5 I get this Jibrish.(look at the upper part, where the File,Edit etc. should be)
[[img]http://img529.imageshack.us/img529/8338/screenshotguitarpro5noname6zp.th.png]](http://img529.imageshack.us/img529/8338/screenshotguitarpro5noname6zp.png)[/img]
its probably missing fonts, so i need a place where to get new fonts

10-My Ubuntu Keeps freezing up on me from time to time and i must reboot to stop it

---

### Post by 2pacalypse on 2006-05-30
any1, please help?

---

### Post by 2pacalypse on 2006-06-01
can any1 please help me with this? (sry for double-posting, but this thread was tossed back a number of pages back, where no one could see it)

---

