---
title: "kernel location?"
date: 2006-02-24
forum: General Help
---

### Post by theduke0 on 2006-02-24
I am trying to install a program that asks for the "kernel source files".  Could anyone point me in the right direction of this folder/files?  

Any help would be appreciated.

---

### Post by jchau on 2006-02-24
[QUOTE=theduke0]I am trying to install a program that asks for the "kernel source files".  Could anyone point me in the right direction of this folder/files?  

Any help would be appreciated.[/QUOTE]


You don't have these files unless you get them.  
See here: [https://wiki.ubuntu.com/KernelHowto#head-889c596f9e064f04b40e8b5d35174c7464be7269](https://wiki.ubuntu.com/KernelHowto#head-889c596f9e064f04b40e8b5d35174c7464be7269)

Hope this helps!

---

### Post by astoltz on 2006-02-24
I think they're in /usr/src/. But unless you've installed them, they're not there by default.```
sudo apt-get install linux-source-2.6.12
```

---

### Post by lamego on 2006-02-24
Do not specify the source version:
Using
```
sudo apt-get install linux-source
```
Will install the source for your current kernel...

---

### Post by astoltz on 2006-02-24
[QUOTE=lamego]Do not specify the source version:
Using
```
sudo apt-get install linux-source
```
Will install the source for your current kernel...[/QUOTE]
But that will keep updating the source package every time a new version is released.  I guess that's usually what you want but just so you're aware. And lamego is right, I should have mentioned that you need the source version that matches your installed kernel version (that's 2.6.12 by default for breezy).

---

