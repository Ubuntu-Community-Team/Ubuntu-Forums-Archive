---
title: "Cannot install xulrunner-1.9.1"
date: 2009-12-13
forum: General Help
---

### Post by xtjacob on 2009-12-13
I'm trying to reinstall xulrunner-1.9.1 on Ubuntu 9.10 64-bit, and when it's reinstalling xulrunner it fails:
```
After this operation, 0B of additional disk space will be used.
Setting up xulrunner-1.9.1 (1.9.1.5+nobinonly-0ubuntu0.9.10.1) ...
/usr/lib/xulrunner-1.9.1.5/xulrunner-bin: error while loading shared libraries: libplds4.so: cannot open shared object file: Error 40
dpkg: error processing xulrunner-1.9.1 (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 xulrunner-1.9.1

```
I'm confused about this, can someone please help! :-|

---

### Post by zvacet on 2009-12-15
Try with 

```
sudo dpkg --configure -a
```

---

### Post by xtjacob on 2009-12-18
Well I solved it. Turned out when I was trying to replace the library I was copying it from my 32-bit Ubuntu VM, so I copied it from a 64-bit version and all was well. :)

---

