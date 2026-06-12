---
title: "Chmod issues"
date: 2011-04-09
forum: General Help
---

### Post by MichealH on 2011-04-09
When Packaging my Python app using ```
dpkg -b
``` I find that it does not work and it comes out with ```
dpkg-deb: control directory has bad permissions 700 (must be >=0755 and <=0775)
```I have tried chmodding the connary/DEBIAN directory as so:
```
sudo chmod -R 755 connary/DEBIAN
```but it does not seem to do anything, can anyone help me? :-)

---

### Post by MichealH on 2011-04-09
[SIZE=4][SOLVED] [/SIZE]

I finds out my USB Flash Drive was formatted as NTFS.... oops.

---

