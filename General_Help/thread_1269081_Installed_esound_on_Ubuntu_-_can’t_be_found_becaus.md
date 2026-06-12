---
title: "Installed esound on Ubuntu - can’t be found because of pkg-config problem?"
date: 2009-09-17
forum: General Help
---

### Post by particleaccelerator on 2009-09-17
I installed the 'esound' package in Ubuntu but when I try to install a separate package that depends on it, it says 'esound' can't be found.
  I googled around and found it might be related to PKG_CONFIG so I set the PKG_CONFIG_PATH like this:
  ```
PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:/usr/lib/pkgconfig
``` However when I look in both of these locations for pkg-config I don't see it.
  And when I try to install pkg-config:
  ```
sudo aptitude install pkg-config
```  I get this output, indicating that nothing seems to be happening:
  ```
lipton@teabag:/usr/lib$ sudo aptitude install pkg-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
  
```However, this package seems to exist because of this:
  ```
lipton@teabag:/usr/lib$ sudo aptitude search pkg-config
i   pkg-config                      - manage compile and link flags for librarie

```Sorry. That's a lot of information. But I'm pretty confused at this point. First day working with Ubuntu.

---

### Post by skatinjj on 2009-09-17
Try this;

```
sudo aptitude update

```
then try installing the package

---

### Post by particleaccelerator on 2009-09-17
Thanks. I had done an update earlier when I first installed Ubuntu.

Tried it again now. But got the same result as above.

"0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded"

I wonder if it's actually installed somewhere but not getting found.

---

### Post by particleaccelerator on 2009-09-17
Actually I just did

sudo aptitude show pkg-config

It says it's installed. Same thing with 'esound'.

But it can't find either of them when I try to install a different package that depends on them.

---

### Post by skatinjj on 2009-09-17
To find out where the packages are installed you can use the find command in a terminal:

```
find . -name "*cow*" -print
```

Replace cow with all or part of the file name.
The * are wild cards in case there is more to the filename in the beginning or end.

---

