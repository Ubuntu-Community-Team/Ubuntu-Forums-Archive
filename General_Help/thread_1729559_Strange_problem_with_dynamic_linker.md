---
title: "Strange problem with dynamic linker"
date: 2011-04-15
forum: General Help
---

### Post by pyp on 2011-04-15
Hello,

I have a 32-bit binary (CA ARCserve backup agent) that I need to get up and running on a AMD64 server.

The binary is dynamically linked...

```
root@foo:/opt/CA/BABcmagt# file caagentd
caagentd: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.0.0, stripped
```... but when I run ldd, I get this:
```
root@foo:/opt/CA/BABcmagt# ldd caagentd
        not a dynamic executable

```And I can't run it, either:
```
root@foo:/opt/CA/BABcmagt# ./caagentd
bash: ./caagentd: No such file or directory

```The same binary runs without problems on a 64-bit SLES 10 machine.

Any ideas?

---

### Post by pyp on 2011-04-15
Ok, I got it.  It seems that the 32-bit versions of glibc and libgcc are not installed by default on Ubuntu 64-bit.

---

