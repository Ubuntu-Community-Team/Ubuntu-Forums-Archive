---
title: "compiling cross gcc"
date: 2011-03-18
forum: General Help
---

### Post by Nexxy on 2011-03-18
Hi ubuntucommunity.

First i want to say that I'm rly new to compiling and compiling gcc.
My plan is to get a cross-gcc-compiler (c,c++) for i686-linux running in VMbox.


[LIST=1]
[*]I installed Ubuntu Server 10.10
[*](im gonna run all the commands as root, to prevent running in any problems with rights, thats cause im not familar with that right and user management of linux)
[*]sudo -s
[*]apt-get update
[*]apt-get upgrade
[*]apt-get dist-upgrade
[*]apt-get install libtool texinfo autoconf gawk build-essentials libc6-dev --fix-missing
[*]restart /reboot my system
[/LIST]
--- Ubuntu is rdy now ---

Now gcc tells me that i shoud have installed binutils , gmp , mpfr and mpc
ok here we go :


[LIST]
[*]downloaded sources for gmp-5.0.1 mpfr-3.0.0 mpc-0.9 binutils-2.21
[*]extract all sources to ~/source
[*]create a new ~/build folder
[*]chdir to ~/build and create gmp mpfr binutils - binutils-i686-cygwin and mpc folder
[*]cd ~/build/gmp && ../../source/gmp-5.0.1/configure
[LIST]
[*]--prefix=/usr/share/tools/gmp
[*]--disable-shared
[/LIST]
 
[*]make && make check && make install (all test passed)
[*]cd ~/build/mpfr && ../../source/mpfr-3.0.0/configure
[LIST]
[*]--prefix=/usr/share/tools/mpfr
[*]--disable-shared
[*]--with-gmp=/usr/share/tools/gmp
[/LIST]
 
[*]make && make check && make install (all test passed)
[*]cd ~/build/mpc && ../../source/mpc-0.9/configure
[LIST]
[*]--prefix=/usr/share/tools/mpc
[*]--disable-shared
[*]--with-gmp=/usr/share/tools/gmp
[*]--with-mpfr=/usr/share/tools/mpfr
[/LIST]
 
[*]make && make check && make install (all test passed)
[/LIST]


[LIST]
[*]cd ~/build/binutils && ../../source/binutils-2.21/configure
[LIST]
[*]--prefix=/usr/share/tools/binutils
[*]--disable-shared
[/LIST]
 
[*]make && make check && make install (all test passed)
[/LIST]


[LIST]
[*]cd ~/build/binutils-i686-cygwin && ../../source/binutils-2.21/configure
[LIST]
[*]--target=i686-cywin
[*]--prefix=/usr/share/tools/binutils
[*]--disable-shared
[/LIST]
 
[*]make && make check && make install (all test passed)
[/LIST]
ok lets go compile gcc now !

[LIST]
[*]cd ~/build/gcc
[/LIST]

[LIST]
[*] ../../source/gcc-4.5.2/configure
[LIST]
[*]--build=i686-linux
[*]--target=i686-cygwin
[*]--host=i686-linux
[*]--disable-nls
[*]--disable-shared
[*]--prefix=/usr/share/tools/x86gcc
[*]--enable-languages=c,c++
[*]--program-prefix=x86win
[*]--with-gnu-ld
[*]--with-gnu-as
[*]--with-gmp=/usr/share/tools/gmp
[*]--with-mpfr=/usr/share/tools/mpfr
[*]--with-mpc=/usr/share/tools/mpc
[*]AS_FOR_TARGET=/usr/share/tools/x86-win/binutils/i686-cygwin/bin/as
[*]LD_FOR_TARGET=/usr/share/tools/x86-win/binutils/i686-cygwin/bin/ld
[*]LD_LIBRARY_PATH=/usr/share/tools/gmp/lib:/usr/share/tools/mpc/lib:/usr/share/tools/mpfr/lib:/usr/share/tools/binutils/lib
[/LIST]
 
[*]configure is doing well
[*]make
[/LIST]
............... but then joining directory gcclib the compilation aborts .. it doesn't find stdio.h
well it search the stdio.h for my target system .. did i miss to do anything like get the targets header first ? but from where ?

[LIST]
[*]/home/nex/build/gcc-build/./gcc/xgcc -B/home/nex/build/gcc-build/./gcc/ -B/usr/share/tools/x86gcc/i686-cygwin/bin/ -B/usr/share/tools/x86gcc/i686-cygwin  /lib/ -isystem /usr/share/tools/x86gcc/i686-cygwin/include -isystem /usr/share/tools/x86gcc/i686-cygwin/sys-include    -g -O2 -O2 -I../../../source/gcc-  4.5.2/gcc/../winsup/w32api/include -I../../../source/gcc-4.5.2/gcc/../winsup/include -I../../../source/gcc-4.5.2/gcc/../winsup/cygwin/include -g -O2 -DI  N_GCC -DCROSS_DIRECTORY_STRUCTURE  -W -Wall -Wwrite-strings -Wcast-qual -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition  -isystem ./incl  ude   -g  -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -Dinhibit_libc  -I. -I. -I../.././gcc -I../../../../source/gcc-4.5.2/libgcc -I../../../../source/gcc-4.5  .2/libgcc/. -I../../../../source/gcc-4.5.2/libgcc/../gcc -I../../../../source/gcc-4.5.2/libgcc/../include  -DHAVE_CC_TLS -DUSE_EMUTLS -o _muldi3.o -MT _  muldi3.o -MD -MP -MF _muldi3.dep -DL_muldi3 -c ../../../../source/gcc-4.5.2/libgcc/../gcc/libgcc2.c \
In file included from ../.././gcc/tm.h:11:0,
                 from ../../../../source/gcc-4.5.2/libgcc/../gcc/libgcc2.c:31:
../../../../source/gcc-4.5.2/libgcc/../gcc/config/i386/cygming.h:103:19: fatal error: stdio.h: No such file or directory
compilation terminated.
make[2]: *** [_muldi3.o] Fehler 1
make[2]: Verlasse Verzeichnis '/home/nex/build/gcc-build/i686-cygwin/libgcc'
[/LIST]
Pls pls help, I'm tryin this about 1 week now to get working.

Thanks in advance
Nexxy

---

### Post by Nexxy on 2011-03-18
is anybody able to transfere this thread into Developing Forums ?

---

### Post by 3Miro on 2011-03-18
Just a guess, but have you installed multilib? Go to Synaptic Package Manager and install gcc-multilib and g++-multilib (for 4.5).

---

### Post by Nexxy on 2011-03-18
ok i installed multilib for gcc and g++ but still nothing happens to my error that hi can't find stdio.h

But thanks for tryin to help me :):D

---

### Post by NumPy on 2011-03-18
> **Nexxy said:**
> ok i installed multilib for gcc and g++ but still nothing happens to my error that hi can't find stdio.h

But thanks for tryin to help me :):D

Why are you using source for gcc ? The repositories should have everything you need to create a build enviroment with the gcc toolkit.
You need build-essential 
```

sudo apt-get install build-essential

```

---

### Post by Nexxy on 2011-03-18
packet build-essential
is already installed :(
any other ideas ? 

I need the i686-cygwin gcc compiler to translate another compiler for ppc-wrs-vxworks (Candian cross compiler)

---

### Post by Nexxy on 2011-03-19
Is there maybe a chance to get the stdio.h + libs from mingw / cywin compiler ?

Does anybody knows deep links to some header - packages ?

---

### Post by NumPy on 2011-03-19
> **Nexxy said:**
> Is there maybe a chance to get the stdio.h + libs from mingw / cywin compiler ?

Does anybody knows deep links to some header - packages ?


What is the output of 
```
which gcc
```

I am thinking you may need mingw, or that your paths are out of whack. 

(the mingw package is gcc-mingw32 by the bye.)

---

### Post by Nexxy on 2011-03-19
hey, thx for your reply 

output of which gcc is 

```
/usr/bin/gcc
```but still same error -> :(
```

/home/nex/build/gcc-build/./gcc/xgcc -B/home/nex/build/gcc-build/./gcc/ -B/usr/share/tools/x86gcc/i686-cygwin/bin/ -B/usr/share/tools/x86gcc/i686-cygwin/lib/ -isystem /usr/share/tools/x86gcc/i686-cygwin/include -isystem /usr/share/tools/x86gcc/i686-cygwin/sys-include    -g -O2 -O2 -I../../../source/gcc-4.5.2/gcc/../winsup/w32api/include -I../../../source/gcc-4.5.2/gcc/../winsup/include -I../../../source/gcc-4.5.2/gcc/../winsup/cygwin/include -g -O2 -DIN_GCC -DCROSS_DIRECTORY_STRUCTURE  -W -Wall -Wwrite-strings -Wcast-qual -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition  -isystem ./include   -g  -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -Dinhibit_libc  -I. -I. -I../.././gcc -I../../../../source/gcc-4.5.2/libgcc -I../../../../source/gcc-4.5.2/libgcc/. -I../../../../source/gcc-4.5.2/libgcc/../gcc -I../../../../source/gcc-4.5.2/libgcc/../include  -DHAVE_CC_TLS -DUSE_EMUTLS -o _muldi3.o -MT _muldi3.o -MD -MP -MF _muldi3.dep -DL_muldi3 -c ../../../../source/gcc-4.5.2/libgcc/../gcc/libgcc2.c \

In file included from ../.././gcc/tm.h:11:0,
                 from ../../../../source/gcc-4.5.2/libgcc/../gcc/libgcc2.c:31:
../../../../source/gcc-4.5.2/libgcc/../gcc/config/i386/cygming.h:103:19: fatal error: stdio.h: No such file or directory

```

---

### Post by NumPy on 2011-03-19
> **Nexxy said:**
> hey, thx for your reply 

output of which gcc is 

```
/usr/bin/gcc
```but still same error -> :(
```

/home/nex/build/gcc-build/./gcc/xgcc -B/home/nex/build/gcc-build/./gcc/ -B/usr/share/tools/x86gcc/i686-cygwin/bin/ -B/usr/share/tools/x86gcc/i686-cygwin/lib/ -isystem /usr/share/tools/x86gcc/i686-cygwin/include -isystem /usr/share/tools/x86gcc/i686-cygwin/sys-include    -g -O2 -O2 -I../../../source/gcc-4.5.2/gcc/../winsup/w32api/include -I../../../source/gcc-4.5.2/gcc/../winsup/include -I../../../source/gcc-4.5.2/gcc/../winsup/cygwin/include -g -O2 -DIN_GCC -DCROSS_DIRECTORY_STRUCTURE  -W -Wall -Wwrite-strings -Wcast-qual -Wstrict-prototypes -Wmissing-prototypes -Wold-style-definition  -isystem ./include   -g  -DIN_LIBGCC2 -D__GCC_FLOAT_NOT_NEEDED -Dinhibit_libc  -I. -I. -I../.././gcc -I../../../../source/gcc-4.5.2/libgcc -I../../../../source/gcc-4.5.2/libgcc/. -I../../../../source/gcc-4.5.2/libgcc/../gcc -I../../../../source/gcc-4.5.2/libgcc/../include  -DHAVE_CC_TLS -DUSE_EMUTLS -o _muldi3.o -MT _muldi3.o -MD -MP -MF _muldi3.dep -DL_muldi3 -c ../../../../source/gcc-4.5.2/libgcc/../gcc/libgcc2.c \

In file included from ../.././gcc/tm.h:11:0,
                 from ../../../../source/gcc-4.5.2/libgcc/../gcc/libgcc2.c:31:
../../../../source/gcc-4.5.2/libgcc/../gcc/config/i386/cygming.h:103:19: fatal error: stdio.h: No such file or directory

```

Even after mingwn install?

---

### Post by Nexxy on 2011-03-20
yep even after installing that package of gcc-mingw32.

I think he's tryin to use the new compiled compiler named xgcc (cross gcc?) in
```
/home/nex/build/gcc-build/gcc/
```[FONT=monospace]
and finaly the params tell us, that he searches stdio.h in this path 
[/FONT]```
-isystem /usr/share/tools/x86gcc/i686-cygwin/include -isystem /usr/share/tools/x86gcc/i686-cygwin/sys-includeshows us that he searches there for some headers which he wont found .. cauz this is the --prefix path :/

```any ideas ?

---

