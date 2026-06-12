---
title: "can't compile epiphany"
date: 2009-10-08
forum: General Help
---

### Post by hantechbl on 2009-10-08
when i try to compile epiphany the terminal says:
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... configure: error: cannot compute suffix of object files: cannot compile
See `config.log' for more details.

attached is a config.log converted to .txt in a compressed format.

---

### Post by Crafty Kisses on 2009-10-08
Do you have build-essential installed?

---

### Post by hantechbl on 2009-10-08
Yes

---

### Post by Joeb454 on 2009-10-09
Thread moved to General Help :)

It looks like the compiler doesn't know what file extension to give certain files, what command are you running to compile epiphany?

---

### Post by hantechbl on 2009-10-10
I think I used make

---

