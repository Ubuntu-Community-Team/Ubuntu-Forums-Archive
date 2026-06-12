---
title: "cannot execute binary file"
date: 2012-08-30
forum: General Help
---

### Post by anythinganyway on 2012-08-30
Hi there! I have just installed a software and I am trying to execute it, but I got:

```
bash: ./sabor: cannot execute binary file
```More information here:

```
$ uname -a
Linux mycomp 2.6.32-42-generic #95-Ubuntu SMP Wed Jul 25 15:57:54 UTC 2012 i686 GNU/Linux

$ file sabor
sabor: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, not stripped

$ ldd sabor
    not a dynamic executable

$ ls -la
-rwxr-xr-x 1  XXX  XXX   554344 2009-07-26 22:25 sabor

```What's the problem here?

---

### Post by steeldriver on 2012-08-30
you're trying to run a 64-bit binary on a 32-bit system?

---

### Post by anythinganyway on 2012-08-30
I just realize that i686 means 32-bit.
Is there any simple solution for that?

---

### Post by greenpeace on 2012-08-30
Have a look where you downloaded the software, they should provide a 32-bit version...

---

### Post by anythinganyway on 2012-08-30
unfortunately, they don't. Any alternative, please?

---

### Post by oldos2er on 2012-08-30
> **anythinganyway said:**
> unfortunately, they don't. Any alternative, please?

Install 64-bit Ubuntu.

---

### Post by anythinganyway on 2012-08-31
I have checked that the CPU of my laptop, intel Centrino Duo, is compatible with 64 bits. But it is more than 5 years ago.Do I have to check whether other components are also compatible with 64 bits?

---

### Post by oldos2er on 2012-08-31
If you're asking about hardware drivers, unless you have some obscure hardware, most if not all should be 64-bit. If you're asking about something else, please clarify.

---

