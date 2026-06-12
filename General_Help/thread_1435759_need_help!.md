---
title: "need help!"
date: 2010-03-21
forum: General Help
---

### Post by mdax138 on 2010-03-21
hello, i'm really interested in using linux and decided to go for ubuntu...

so i went to the mainpage, downloaded the netbook remix, created a bootable flash drive using unetbootin, my netbook can already read it, and it's all perfectly well... already fix the bugs "could not find kernel image" and "could not find ramdisk" thanks to other existing threads...

so when i'm already in the installer boot menu, i press press enter to boot, then the page goes black, then after a short while it kind of restarts and then i find myself in the installer boot menu again... then when i boot again, it just repeats itself... there is no error, i don't know what's happening, can anyone help me with this?

by the way, my netbook is msi wind u160 with an upgraded ram and a windows 7 starter os... if there are any problems with the specifications or technical errors or anything... please tell me... i'm new at this... thanks...

---

### Post by dcstar on 2010-03-21
> **mdax138 said:**
> 
.......
so when i'm already in the installer boot menu, **i press press enter to boot**, then the page goes black, then after a short while it kind of restarts and then i find myself in the installer boot menu again... then when i boot again, it just repeats itself... there is no error, i don't know what's happening, can anyone help me with this?


Why are you "booting" at a boot menu, don't you want to install?

---

### Post by mdax138 on 2010-03-22
wow... I honestly don't know. so how do i install it?

---

### Post by ndefontenay on 2010-03-22
Hi.

few question before you install:

1) Do you have some extra unpartitioned disk space on which you can install? It can be on the same Hard disk or on a different one.

If you don't have unpartitioned disk pace, you can shrink your existing partition inside windows disk manager. That will leave an empty space that you can use when you finally decide to install linux.

If you don't want to free any space at all, you can install from within windows using wubi. Not my favorite but apparently a good choice for beginners.

If you do have an unpartitioned disk space:

1) Insert your CD
2) Boot from the CD. 
3) Choose option Install Ubuntu
4) When you got to pick where to install it: Choose install ubuntu on the next contiguous empty space (The option shows only if you have some unpartitioned space)
5) Complete installation
6) At the end remove your CD and restart your computer

You will have a boot loader called Grub which will give you the option between windows and ubuntu. Ubuntu being at the very top, just press enter.

Enjoy !

Nico

---

### Post by ndefontenay on 2010-03-22
last bit of advice. Shrinking your windows partition is pretty safe but it does move your files around your hard disk to free space. So if you are the unlucky one you can loose said partition. If you have sensitive data on the disk you are going to work with, backup your data on an external hard drive.

---

