---
title: "installing CEImagesetEditor-0.7.1"
date: 2011-05-30
forum: General Help
---

### Post by hgbso on 2011-05-30
this is my problem


> root@ubuntu:~/Programming/CEImagesetEditor-0.7.1# make
make: *** No targets specified and no makefile found.  Stop.
root@ubuntu:~/Programming/CEImagesetEditor-0.7.1# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for CEGUI... configure: error: Package requirements (CEGUI-OPENGL >= 0.7.0) were not met:




> Requested 'CEGUI-OPENGL >= 0.7.0' but version of CEGUI is 0.6.2

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CEGUI_CFLAGS
and CEGUI_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

