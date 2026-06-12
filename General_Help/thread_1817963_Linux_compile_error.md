---
title: "Linux compile error"
date: 2011-08-04
forum: General Help
---

### Post by fered on 2011-08-04
Hi;
I have following error in compile process:
     
     ```
fs/binfmt_aout.c: Assembler messages:
fs/binfmt_aout.c:156: Error: suffix or operands invalid for `cmp'
make[2]: *** [fs/binfmt_aout.o] Error 1
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/home/ali/Desktop/linux-2.6.14'
make: *** [debian/stamp/build/kernel] Error 2 
kernel version: 2.6.14
distribution: ubuntu 10.04
gcc: 4.4

```
When I used kernel 2.6.39 or downgrade gcc, I had same error.

Thanks.

---

