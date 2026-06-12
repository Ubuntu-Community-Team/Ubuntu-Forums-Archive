---
title: "No wireless driver (bcm43xx) after installing 9.10"
date: 2009-10-31
forum: General Help
---

### Post by rugbert on 2009-10-31
So I just did a fresh install but guess what? no wifi. Thats normal tho, the bcm43 card I have requires a restricted driver. BUT when I went to the restricted hardware wizard nothing shows up :/

---

### Post by dummy910 on 2009-10-31
it should be listed in your synaptic package manager.

to install from terminal:
```
sudo apt-get install bcmwl-kernel-source
```
then install:
```
sudo apt-get install linux-backports-modules-karmic
```
then
restart reboot and you should now have wireless.

---

### Post by rugbert on 2009-11-01
I dont have wireless actually, the driver now shows up in my restricted hardware list but it says: the driver is activated but is not currently in use.

My wireless switch is toggled but its not working.

---

