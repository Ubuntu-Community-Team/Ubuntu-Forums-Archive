---
title: "Formating a Partition in Ubuntu 10.10"
date: 2010-11-21
forum: General Help
---

### Post by the wolfe on 2010-11-21
Is there any way to partition off say 40GB of a 250GB drive (only 5GB used) into an NTFS partition to install windows Vista SP1?? I have tried the System -> administration -> disk utility, but I can not figure out how to partition in it. 
Thanks ahead of time for your help.

---

### Post by mika0110 on 2010-11-21
you want to creat new partition or change type of partition?

---

### Post by dcstar on 2010-11-21
> **the wolfe said:**
> Is there any way to partition off say 40GB of a 250GB drive (only 5GB used) into an NTFS partition to install windows Vista SP1?? I have tried the System -> administration -> disk utility, but I can not figure out how to partition in it. 
Thanks ahead of time for your help.

gparted

---

### Post by drewsus on 2010-11-21
Well, I prefer Gparted:
```
sudo apt-get install gparted
```

GIve that a go. But youd have to do it from a Live CD/USB if you wanted to do it with your drive that has Ubuntu installed (can't do it while it is mounted and can't unmounted if you are running your system from it). 

Right click on what you wanted to resize, select resize. But you will have to reinstate grub cuz the new Windows install will overwrite it.
Search google for installing windows after ubuntu.

---

### Post by the wolfe on 2010-11-21
> **mika0110 said:**
> you want to creat new partition or change type of partition?
Create a new partition. I want to keep Ubuntu, and install Vista SP1 to use my games on it. 

> **drewsus said:**
> Well, I prefer Gparted:
```
sudo apt-get install gparted
```

GIve that a go. But youd have to do it from a Live CD/USB if you wanted to do it with your drive that has Ubuntu installed (can't do it while it is mounted and can't unmounted if you are running your system from it). 

Right click on what you wanted to resize, select resize. But you will have to reinstate grub cuz the new Windows install will overwrite it.
Search google for installing windows after ubuntu.
what is grub and how would I reinstate it? 

I am going to figure this all out before I try, as I dont have any other usable computer to post up the issues that arise.

---

### Post by drewsus on 2010-11-22
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

[http://ubuntuforums.org/showthread.php?t=1627815](http://ubuntuforums.org/showthread.php?t=1627815)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by the wolfe on 2010-11-22
ok, thanks.

---

### Post by oldfred on 2010-11-22
Make sure you create a primary partition for NTFS with the boot flag. Windows will not install otherwise.

---

