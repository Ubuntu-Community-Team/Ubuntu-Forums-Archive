---
title: "Error message while installing application"
date: 2010-04-25
forum: General Help
---

### Post by bashphoenux on 2010-04-25
everytime I try to install an application I get this:
```
sudo apt-get install gsmart
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package opera needs to be reinstalled, but I can't find an archive for it
```
what should I do?
I try to reinstall opera but when I double the .deb package it says unable to install/ the package may be damaged and I have downloaded a fresh copy for about 4 times now!
what to do?

---

### Post by dino99 on 2010-04-25
install locate

then into console : locate opera

sudo apt-get install -f  to find errors

you should be able to remove/purge opera then reinstall it ( i suppose you have opera installed, if so first export your bookmarks and passwords if any before removing it)

---

### Post by bashphoenux on 2010-04-25
> **dino99 said:**
> install locate

then into console : locate opera

sudo apt-get install -f  to find errors

you should be able to remove/purge opera then reinstall it ( i suppose you have opera installed, if so first export your bookmarks and passwords if any before removing it)
I get ```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package opera needs to be reinstalled, but I can't find an archive for it.

``` error when I do sudo apt-get install -f

---

### Post by dino99 on 2010-04-25
what give: locate opera ? is it really installed ?

---

### Post by bashphoenux on 2010-04-25
yes there is an opera installed , I tried installing a newer version of opera using .deb file when it showed some error and since then i am facing this problem

---

### Post by dino99 on 2010-04-25
so file are corrupted, see two ways to work around:

- save what you need then delete the install one before to reinstall
- or create a new user and boot with it, then try to install again

---

### Post by bashphoenux on 2010-04-25
> **dino99 said:**
> so file are corrupted, see two ways to work around:

- save what you need then delete the install one before to reinstall
- or create a new user and boot with it, then try to install again


sudo apt-get remove opera doesn't work it shows the same error message again

---

### Post by bashphoenux on 2010-04-25
i get this
[[IMG]http://img215.imageshack.us/img215/475/errorxx.jpg[/IMG]](http://img215.imageshack.us/i/errorxx.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)
when i run update manager(alt+f2->update)

---

