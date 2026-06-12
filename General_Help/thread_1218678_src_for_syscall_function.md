---
title: "src for syscall function"
date: 2009-07-20
forum: General Help
---

### Post by Sebrent_Tehroth on 2009-07-20
In FreeBSD I found the source code for the [font=courier new]syscall[/font] function in [font=courier new]/usr/src/sys/i386/i386/trap.c[/font]

**Where can I find the equivalent source code for the _[font=courier new]syscall[/font]_ function in Ubuntu?**

I've been searching through [font=courier new]/usr/src/linux-source-2.6.24/arch/x86[/font] for a while now, grep-ing quite a bit and can not find it. (Is it named something else in Ubuntu/Linux?)

I'm looking for the actual code for handling system calls in Ubuntu, not the header file nor list of system calls.

Thank you in advance.

---

### Post by Sebrent_Tehroth on 2009-07-22
I believe I finally found my answer ... here it is for anyone else that may have this question:

There is a 32-bit and a 64-bit version ... and these are for the x86 architecture

/usr/src/linux/arch/x86/kernel/entry_32.S
/usr/src/linux/arch/x86/kernel/entry_64.S

From entry_32.s: "entry.S contains the system-call and fault low-level handling routines."

---

