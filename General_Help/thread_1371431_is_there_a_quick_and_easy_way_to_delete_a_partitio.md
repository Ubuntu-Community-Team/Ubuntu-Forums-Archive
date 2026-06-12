---
title: "is there a quick and easy way to delete a partition without formatting"
date: 2010-01-03
forum: General Help
---

### Post by blackmajik2021 on 2010-01-03
Ive got two partitions of xubuntu installed and I only want one. Is there I way I can just delete the one i dont want and use that extra space for the other? 

also, how would i know which is which when deleting?

---

### Post by Leppie on 2010-01-03
are these partitions on the system you're using now?
then post your /etc/fstab and the output of "sudo fdisk -l" (a lowercase l, not number 1)

---

### Post by blackmajik2021 on 2010-01-03
yup, Im an idiot and installed two partitions of the exact same thing when formatting, so now I have two duplicated of xubuntu 9.10 with only half the hard drive space.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4ecf4ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7342    58974583+  83  Linux
/dev/sda2            7343       14593    58243657+   5  Extended
/dev/sda5           14503       14593      730926   82  Linux swap / Solaris
/dev/sda6            7343       14411    56781679+  83  Linux
/dev/sda7           14412       14502      730926   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by Leppie on 2010-01-03
actually, if you open gparted (System>Administration>Gparted), you will be able to see all the partitions on your system. you can remove the one you don't want anymore.
resizing will have to be done when you're system is not live, otherwise just use the freed-up space for an extra partition and mount it.

---

### Post by chaanakya_chiraag on 2010-01-03
Basically, you will need to go into GParted.  If you don't have a "Partition Editor" menu item in System->Administration, go to the terminal and run ```
sudo aptitude install gparted
```Next, go to System->Administration->Partition Editor and let it load.  Do all of this **in the actual install** because otherwise you won't know which one you are deleting!  Select the partition that is not locked, right-click and select "Delete".  Apply that operation.  After that finishes, **boot into a live CD**, open GParted (you may have to install it first because now it's running off the cd) and expand the remaining Xubuntu partition to fill the whole hard disk :)  You're done :)

---

### Post by blackmajik2021 on 2010-01-03
xubuntu doesnt come with gparted...i needed to download it...its for gnome though and xubuntu uses xfce...will that be a problem?

---

### Post by chaanakya_chiraag on 2010-01-03
No, it will still be available in your package management system.  That's the beauty of Linux :)

---

### Post by blackmajik2021 on 2010-01-03
> **chaanakya_chiraag said:**
> Basically, you will need to go into GParted.  If you don't have a "Partition Editor" menu item in System->Administration, go to the terminal and run ```
sudo aptitude install gparted
```Next, go to System->Administration->Partition Editor and let it load.  Do all of this **in the actual install** because otherwise you won't know which one you are deleting!  Select the partition that is not locked, right-click and select "Delete".  Apply that operation.  After that finishes, **boot into a live CD**, open GParted (you may have to install it first because now it's running off the cd) and expand the remaining Xubuntu partition to fill the whole hard disk :)  You're done :)

this is all fine but i think my computer will be too slow to run off the live cd...i only have 256 mb ram.

---

### Post by Leppie on 2010-01-03
> **blackmajik2021 said:**
> xubuntu doesnt come with gparted...i needed to download it...its for gnome though and xubuntu uses xfce...will that be a problem?

i believe that xubuntu by default installs both qt and gtk libraries. this enables you to use apps from both the kde and gnome desktop environments (but not all applications of course) without installing these desktops.

---

### Post by chaanakya_chiraag on 2010-01-03
Sorry, but that's the only way I know of expanding a partition that is used while running the operating system :(

---

### Post by blackmajik2021 on 2010-01-03
g parted was a success...now im just looking for an alternative to the live cd step

---

### Post by Leppie on 2010-01-03
> **blackmajik2021 said:**
> this is all fine but i think my computer will be too slow to run off the live cd...i only have 256 mb ram.

the xubuntu livecd requirement is 192mb.

---

### Post by chaanakya_chiraag on 2010-01-03
Also, the live cd doesn't need to be ubuntu...you could use **any** Linux live cd and it would work, providing it has gparted or some other partitioner.

---

### Post by chaanakya_chiraag on 2010-01-03
Therefore, you could use Damn Small Linux or something like that, which has really tiny requirements, if you're really pushed for RAM/CPU/other stuff

---

