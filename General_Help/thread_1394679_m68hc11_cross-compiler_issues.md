---
title: "m68hc11 cross-compiler issues"
date: 2010-01-30
forum: General Help
---

### Post by think13 on 2010-01-30
For the past couple of days I have been trying to get a cross-compiler/assembler for the m68hc11 to work in Ubuntu.

First, I tried to install the packages gcc-m68hc1x, binutils-m68hc1x, gdb-m68hc1x from the repository. The assembler didn't work for me in that package, because m68hc11-as (or whatever it's called) didn't seem to accept my assembly code format. It thought labels were opcodes (even though they started in column 1) and didn't recognize constants like $2000. as -m68hc11 gives 'unrecognized option -m68hc11' even though that option is listed in the as man page.

I also tried to install from the GNU 68HC11 toolchain website ([http://www.gnu-m68hc11.org/m68hc11_download.php](http://www.gnu-m68hc11.org/m68hc11_download.php)), both from source and using alien on the .rpm's they provide. When installing from the rpms, m6811-elf-gcc worked, but not gcc -m68hc11 (again the unrecognized option error). This is a problem because I can't make the GNU Embedded Libraries ([http://gel.sourceforge.net/](http://gel.sourceforge.net/)) without gcc -m68hc11 (which is used extensively in the make process for gel).

At this point, I'm thinking I may need to compile binutils and gcc from source, configuring them to support m68hc11 cross-compilation (I'm thinking they aren't configured for this support when compiled for Ubuntu), which I'm not particularly excited about attempting.

---

