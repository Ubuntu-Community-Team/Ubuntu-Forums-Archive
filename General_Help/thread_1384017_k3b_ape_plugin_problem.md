---
title: "k3b ape plugin problem"
date: 2010-01-17
forum: General Help
---

### Post by agreatguy6 on 2010-01-17
So I downloaded the necessary file, followed all the instructions as written on the tutorial elsewhere in the forums.
Everything's going smoothly until ./configure.

I get: 
> desktop:~/k3bmonkeyaudioplugin-3.1$ ./configure
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
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wno-non-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.


how do I fix this?

Better yet, is there an easier way to burn a CD from an ape and cue?

---

### Post by jamesisin on 2010-01-17
I convert all my ape files to flac files:

[http://www.soundunreason.com/InkWell/?p=1282](http://www.soundunreason.com/InkWell/?p=1282)

---

### Post by agreatguy6 on 2010-01-17
> **jamesisin said:**
> I convert all my ape files to flac files:

[http://www.soundunreason.com/InkWell/?p=1282](http://www.soundunreason.com/InkWell/?p=1282)

I have been too, in foobar, but it's so time consuming. 
What Im looking for is something that I can just be like "hey, here's an .ape file, here's the .cue." and it'll take it and make me a CD.

---

### Post by jamesisin on 2010-01-18
Well, there is always running Monkey Audio under WINE...

---

### Post by agreatguy6 on 2010-01-18
Monkey's Audio, for some reason, doesn't want to open on my computer.
Foobar doesn't burn CDs [I've heard there's a way to make it, though] and GnomeBaker doesn't recognize ape or cue files.

---

### Post by jamesisin on 2010-01-18
I haven't finished my post on converting ape files directly into flac files (without splitting).  I know; I know: what a lazy battered.

I'll post the link when I have it ready.  There is a bash script involved.  It might help.

---

### Post by agreatguy6 on 2010-01-18
> **jamesisin said:**
> I haven't finished my post on converting ape files directly into flac files (without splitting).  I know; I know: what a lazy battered.

I'll post the link when I have it ready.  There is a bash script involved.  It might help.

Gracias :)

---

### Post by jamesisin on 2010-01-18
Here it is:

[http://www.soundunreason.com/InkWell/?p=1335](http://www.soundunreason.com/InkWell/?p=1335)

The script itself is really basic.  It involves getting two other files (all three end up in /usr/local/bin).

Let me know if you have any questions (either here or there).

There are several other things you could do to automate the conversion process (like running a cron job nightly on some specific folder which launched this script, thus converting all the apes overnight while you sleep).

---

### Post by agreatguy6 on 2010-01-19
Thanks!

---

