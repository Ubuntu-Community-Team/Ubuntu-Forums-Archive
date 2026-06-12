---
title: "DMTCP Install not happening; any checkpointing suggestions?"
date: 2009-09-11
forum: General Help
---

### Post by karasuman on 2009-09-11
I'm trying to install the checkpointing program DMTCP, which can be found at [http://dmtcp.sourceforge.net/]("http://dmtcp.sourceforge.net/").  The documentation claims that the program runs on Ubuntu, but I get an error while following the installation instructions.  I would appreciate any advice or ideas about what's going wrong or how to get checkpointing going on Ubuntu.

Here's the short version of what I'm doing with the file with the error at the end:

```
./configure
beth@cheerbear-netbook:~/Desktop/dmtcp_1.05-r343$ make
(cd mtcp && make CC=gcc build readmtcp)
make[1]: Entering directory `/home/beth/Desktop/dmtcp_1.05-r343/mtcp'
rm -f mtcp.t
ld -shared --verbose > mtcp.t
cat mtcp.t | sed -e '1,/========================/ d' > mtcp.tmp
cat mtcp.tmp | sed -e '/========================/,$ d' > mtcp.t
rm -f mtcp.tmp mtcp.t-fail
if test `uname -m` = x86_64; then \
	  if patch mtcp.t mtcp.t.patch-x86_64; then \
	    :; \
	  else \
	    mv mtcp.t mtcp.t-fail; false; \
	  fi \
	else \
	  if patch mtcp.t mtcp.t.patch-i386; then \
	    :; \
	  else \
	    mv mtcp.t mtcp.t-fail; false; \
	  fi \
	fi
/bin/sh: patch: not found
make[1]: *** [mtcp.t] Error 1
make[1]: Leaving directory `/home/beth/Desktop/dmtcp_1.05-r343/mtcp'
make: *** [mtcp] Error 2

```

Here's the complete output:

```
beth@cheerbear-netbook:~/Desktop/dmtcp_1.05-r343$ ./configure
checking whether make sets $(MAKE)... yes
checking whether ln -s works... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
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
checking for readline in -lreadline... no
checking for gcl... no
configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  'Makefile.in' seems to ignore the --datarootdir setting
config.status: creating test/Makefile
config.status: creating test/testconfig.py
=== configuring in dmtcp (/home/beth/Desktop/dmtcp_1.05-r343/dmtcp)
configure: running /bin/bash ./configure --disable-option-checking '--prefix=/usr/local'  --cache-file=/dev/null --srcdir=.
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
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
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
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
checking whether gcc and cc understand -c and -o together... no
checking for ranlib... ranlib
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/config.h
config.status: src/config.h is unchanged
config.status: executing depfiles commands
[1]+  Done                    gedit INSTALL
beth@cheerbear-netbook:~/Desktop/dmtcp_1.05-r343$ make
(cd mtcp && make CC=gcc build readmtcp)
make[1]: Entering directory `/home/beth/Desktop/dmtcp_1.05-r343/mtcp'
rm -f mtcp.t
ld -shared --verbose > mtcp.t
cat mtcp.t | sed -e '1,/========================/ d' > mtcp.tmp
cat mtcp.tmp | sed -e '/========================/,$ d' > mtcp.t
rm -f mtcp.tmp mtcp.t-fail
if test `uname -m` = x86_64; then \
	  if patch mtcp.t mtcp.t.patch-x86_64; then \
	    :; \
	  else \
	    mv mtcp.t mtcp.t-fail; false; \
	  fi \
	else \
	  if patch mtcp.t mtcp.t.patch-i386; then \
	    :; \
	  else \
	    mv mtcp.t mtcp.t-fail; false; \
	  fi \
	fi
/bin/sh: patch: not found
make[1]: *** [mtcp.t] Error 1
make[1]: Leaving directory `/home/beth/Desktop/dmtcp_1.05-r343/mtcp'
make: *** [mtcp] Error 2

```

---

### Post by karasuman on 2009-09-11
So, I compared my configuration output with that of a computer that did this successfully.  In order to get this going, I was missing two things: the patch package and the g++ package.

The following were sufficient to get checkpointing going:

```
sudo apt-get install patch
sudo apt-get install g++
./configure
sudo make
sudo make install
```

---

