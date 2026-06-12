---
title: "C programs compile error"
date: 2009-12-22
forum: General Help
---

### Post by clinus on 2009-12-22
Hi,
I'm trying to compile c source file but I'm getting errors, I'm pasting them below
c-nna@c-nna-lapy:~$ cc -o helo helo.c
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/../lib/libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.4.1/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status

can any one help to resolve this problem, how to compile and run c/c++ source files

I've tried cc -c and gcc also, how can I resolve this problm?
Thanks

---

### Post by jithendra89 on 2009-12-22
i think there's samethng wrong with your c libraries..

---

### Post by Queue29 on 2009-12-22
Is 4.4.1 still the version of gcc ubuntu is shipping with?

---

### Post by jithendra89 on 2009-12-22
> **Queue29 said:**
> Is 4.4.1 still the version of gcc ubuntu is shipping with?

its 4.3.3 in ubuntu 9.04

---

