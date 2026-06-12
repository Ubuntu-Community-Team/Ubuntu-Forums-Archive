---
title: "gDesklets-0.35.3"
date: 2006-03-02
forum: General Help
---

### Post by armyrebel on 2006-03-02
Im having a problem installing the program  here is the output for it:

root@ubuntu:/home/rex/gDesklets-0.35.3# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
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
checking for gcc... gcc
checking whether we are using the GNU C++ compiler... yes
checking whether gcc accepts -g... yes
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for perl... /usr/bin/perl
[B]checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
[/B]

I have the perl there..So what do i tdo

---

### Post by cronholio on 2006-03-02
Why do you build it from source? Go to System->Administration->Synaptic, Search for gdesklets and install it.

If you need to build it from source, install libxml-parser-perl (also through Synaptic).

---

### Post by Xian on 2006-03-02
Get all the deps beforehand...

$ sudo apt-get build-dep gdesklets

---

### Post by armyrebel on 2006-03-02
I dont have internet on that computer.  So im doing it one step at a time.  I have to download the .debs onto thumb drive.

---

