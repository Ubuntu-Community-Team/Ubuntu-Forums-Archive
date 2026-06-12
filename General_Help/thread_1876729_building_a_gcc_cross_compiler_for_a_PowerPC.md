---
title: "building a gcc cross compiler for a PowerPC"
date: 2011-11-06
forum: General Help
---

### Post by dex87 on 2011-11-06
Could someone please explain to me in general terms what I should do to get this working?

I compiled both gcc and binutils with --target=powerpc-linux-elf and --prefix=/home/ppc-compiler and installed them both to that location.

Now the binaries work fine, except for one problem. Whenever I try to compile c code, the linker says it can't find the c libraries, and when I explicitly tell it the location of the c libraries, it says they are not compatible.

So, does this mean I have to compile glibc as well? If so, could anyone please help me on compiling it and then integrating it with the gcc and binutils I compiled before? I really don't know where to begin. Thanks!

---

