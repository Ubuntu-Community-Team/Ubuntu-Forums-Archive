---
title: "Synaptic Package Manager broke"
date: 2009-08-17
forum: General Help
---

### Post by edhawk2 on 2009-08-17
Running 8.04, when I  tried to open Synaptic, I get the following error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Synaptic was working fine and all of a sudden this.  On a single user system, if I'm not the "superuser" who is?

When I try to run "dkpg --..." it wants a superuser permission.  I'm lost.

---

### Post by Soul-Sing on 2009-08-17
Its only sudo you need..thats all
so: ```
sudo dpkg --configure -a
```
in the terminal.

---

### Post by Soul-Sing on 2009-08-17
> **leoquant said:**
> Its only sudo you need..thats all
so: ```
sudo dpkg --configure -a
```
in the terminal.

then: enter===> password: enter

---

