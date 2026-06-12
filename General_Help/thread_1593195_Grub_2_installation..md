---
title: "Grub 2 installation."
date: 2010-10-11
forum: General Help
---

### Post by harivittal.hk on 2010-10-11
Hi.
I am trying to install upgraded version of grub i.e ver 1.96.
I got this msg from the console, i'm not able to figure out what it says about the packages thats going to be removed,will that uninstall java??:confused:,can anybody plz help.
I ran d cmd : sudo aptitude install grub-pc...then
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  libjline-java{u} linux-headers-2.6.31-14{u} 
  linux-headers-2.6.31-14-generic{u} rhino{u} 
0 packages upgraded, 0 newly installed, 4 to remove and 89 not upgraded.
Need to get 0B of archives. After unpacking 83.0MB will be freed.
Thank all.

---

### Post by dino99 on 2010-10-11
are you running Lucid ?

you can goes on with the previous command, all is fine, after installing grub-pc you will update the other packages as well.

---

### Post by harivittal.hk on 2010-10-11
> **dino99 said:**
> are you running Lucid ?

you can goes on with the previous command, all is fine, after installing grub-pc you will update the other packages as well.

I'm using Karmic.

---

### Post by dino99 on 2010-10-11
oh grub-pc is available on Karmic :P

In that case remove/purge grub (grub-legacy) and menu.lst, then install grub-pc

---

### Post by harivittal.hk on 2010-10-11
> **dino99 said:**
> oh grub-pc is available on Karmic :P

In that case remove/purge grub (grub-legacy) and menu.lst, then install grub-pc

If i ckeck with this cmd: "grub -install -v" its saying the program "grub" is not installed on your system, and says can be installed by sudo apt-get...why is it like this??
Its not recognizing either purge or remove commands also...

---

### Post by Quackers on 2010-10-11
Read drs305's guide below
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

