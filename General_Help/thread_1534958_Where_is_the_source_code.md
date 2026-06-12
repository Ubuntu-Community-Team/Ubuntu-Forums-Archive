---
title: "Where is the source code?"
date: 2010-07-20
forum: General Help
---

### Post by BurningSludge on 2010-07-20
[FONT=Comic Sans MS][SIZE=3]I have been using Linux for 2 months, specifically Ubuntu, and been wondering where the source code is. Not only do I wonder where the kernel source code is but also where the source code for the installed programs are.[/SIZE][/FONT]

---

### Post by valbaca on 2010-07-20
[http://archive.ubuntu.com/](http://archive.ubuntu.com/)
 
You can also get source for individual packages:
```
 
 
sudo apt-get build-dep $package

```
where package=whatever package you want.
 
then do 
```
sudo apt-get source $package
```
to get the source for that package.

---

### Post by oldos2er on 2010-07-20
Enable the source code repository via menus System, Administration, Software Sources.

---

