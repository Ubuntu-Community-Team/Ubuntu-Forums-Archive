---
title: "complier used to compile the kernel"
date: 2006-02-01
forum: General Help
---

### Post by youbaji on 2006-02-01
What's the version of gcc used to compile the official ubuntu kernel?
I am to install a module which requires the gcc of the same version compile the kernel.
Thanks!

---

### Post by codejunkie on 2006-02-01
[QUOTE=youbaji]What's the version of gcc used to compile the official ubuntu kernel?
I am to install a module which requires the gcc of the same version compile the kernel.
Thanks![/QUOTE]
gcc-3.4

---

### Post by hw-tph on 2006-02-02
It depends on what kernel you run. You should be able to find out by typing **cat /proc/version**. It will produce output similar to this: ```
Linux version 2.6.15-ck3-devon (root@devon) (gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)) #1 PREEMPT Tue Jan 31 20:34:37 CET 2006
```


Håkan

---

### Post by az on 2006-02-02
"That will never happen again!"


That is what Matt Zimmerman said in response to the remark that gcc-3.4 is not on the install cd.  This is a pain for users who need a kernel module to get onto the net in order to be able to download gcc-3.4......

---

