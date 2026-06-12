---
title: "make error 1 help"
date: 2009-11-09
forum: General Help
---

### Post by FraggedLocust on 2009-11-09
I'm trying to get my Dream Cheeky USB missile launcher to work with Ubuntu. I found a solution that may work, but I'm having problems getting the source to compile. I'm using the library found [here]("http://kim.tensta.gannert.se/projects/launcher/"), and I've installed the wxWidgets 2.8 (I think). When I run ./configure, I get this output:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for wx-config... /usr/bin/wx-config
checking for wxWidgets version >= 2.6.0... yes (version 2.8.10)
checking for wxWidgets static library... no
checking if debugging is enabled... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/console/Makefile
config.status: creating src/control/Makefile
config.status: creating src/include/Makefile
config.status: creating src/lib/Makefile
config.status: creating src/tests/Makefile
config.status: creating src/include/config.h
config.status: src/include/config.h is unchanged
config.status: executing depfiles commands
```

and trying to run make gives me this:

```
Making all in src
make[1]: Entering directory `/home/wade/Downloads/launcher-1.0/src'
Making all in lib
make[2]: Entering directory `/home/wade/Downloads/launcher-1.0/src/lib'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/wade/Downloads/launcher-1.0/src/lib'
Making all in include
make[2]: Entering directory `/home/wade/Downloads/launcher-1.0/src/include'
make  all-am
make[3]: Entering directory `/home/wade/Downloads/launcher-1.0/src/include'
make[3]: Leaving directory `/home/wade/Downloads/launcher-1.0/src/include'
make[2]: Leaving directory `/home/wade/Downloads/launcher-1.0/src/include'
Making all in console
make[2]: Entering directory `/home/wade/Downloads/launcher-1.0/src/console'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include     -g -O2 -MT lconsole.o -MD -MP -MF ".deps/lconsole.Tpo" -c -o lconsole.o lconsole.c; \
	then mv -f ".deps/lconsole.Tpo" ".deps/lconsole.Po"; else rm -f ".deps/lconsole.Tpo"; exit 1; fi
lconsole.c:9:31: error: readline/readline.h: No such file or directory
lconsole.c:10:30: error: readline/history.h: No such file or directory
lconsole.c: In function ‘run’:
lconsole.c:391: warning: assignment makes pointer from integer without a cast
make[2]: *** [lconsole.o] Error 1
make[2]: Leaving directory `/home/wade/Downloads/launcher-1.0/src/console'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/wade/Downloads/launcher-1.0/src'
make: *** [all-recursive] Error 1
```

What packages should I have installed to make sure I have wxWidgets installed properly?

---

### Post by michy99 on 2009-11-09
Apparently, you need readline/readline.h and readline/history.h which are in either libreadline5-dev or libreadline6-dev.

---

### Post by FraggedLocust on 2009-11-09
had libreadline6-dev, added libreadline-dev, which seemed to get rid of that error. New error seems to be in the code:

```
lcontrol.cc:180: error: ISO C++ forbids declaration of ‘wxNotebook’ with no type
lcontrol.cc:180: error: expected ‘;’ before ‘*’ token
lcontrol.cc: In constructor ‘ControlDialog::ControlDialog()’:
lcontrol.cc:187: error: class ‘ControlDialog’ does not have any field named ‘book’
lcontrol.cc:187: error: expected type-specifier before ‘wxNotebook’
lcontrol.cc:187: error: expected ‘)’ before ‘wxNotebook’
lcontrol.cc:189: error: ‘book’ was not declared in this scope

```

Can I edit those errors out of the code, or am I still missing something?

---

