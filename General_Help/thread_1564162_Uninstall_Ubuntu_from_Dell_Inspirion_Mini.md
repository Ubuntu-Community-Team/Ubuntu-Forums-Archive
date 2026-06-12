---
title: "Uninstall Ubuntu from Dell Inspirion Mini"
date: 2010-08-30
forum: General Help
---

### Post by jakesch on 2010-08-30
How would I go about uninstalling Ubuntu from my netbook and resizing the partitions all back onto my windows c: partition? I have no XP installation cd to use or usb setup for XP installation.
I want to get my netbook back to windows because I want to setup Ubuntu on my main laptop. Thanks in advanced.

---

### Post by migs73 on 2010-08-30
You can run Gparted from the Ubuntu Live CD.

---

### Post by lmarmisa on 2010-08-30
I suppose you have a dual boot XP + Ubuntu system.

It would be interesting to see how are defined the partitions of your hard drive.

Please, open a terminal, type this comand and show us its output:

```

sudo fdisk -l

```Gparted is a good tool for deleting the Linux and swap partitions, but you will need to restore the XP boot loader of the Master Boot Record MBR of your hard drive too. 

An Ubuntu Live CD is required for both operations.

---

