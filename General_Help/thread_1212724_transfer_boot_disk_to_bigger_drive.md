---
title: "transfer boot disk to bigger drive?"
date: 2009-07-14
forum: General Help
---

### Post by cnschulz on 2009-07-14
Hi, 

Im sure this has been asked before but i cant find it...

I would like to transfer the contents of my boot disk to a new drive. The new drive is larger than the old one. Im sure this is possible but im running console only so please dont say "use gparted" :-)

Existing boot disk 80Gb Intreped server install
New disk 120GB

- Obviously id like to boot from the new disk and throw away the old disk
- I dont want to do a fresh install... i want to tarball the existing boot drive and use that
- id like to reclaim the additional 40gb of space into the boot partition to make things simpler to manage.

thanks for any help.

c.

---

### Post by prshah on 2009-07-14
> **cnschulz said:**
> 
I would like to transfer the contents of my boot disk to a new drive. The new drive is larger than the old one. Im sure this is possible but im running console only 


Take a look at [[SOLVED] Exact duplicate of entire HDD]("http://ubuntuforums.org/showthread.php?t=874643") for full details; post back if you need clarifications.

---

### Post by cnschulz on 2009-07-14
ahhh yes! thank you!

once the image is transfered what is the simplest way to increase the size of the partition? or will dd "just do it"?

cheers

c.

---

### Post by ericab on 2009-07-14
clonezilla is all you need.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by prshah on 2009-07-14
> **cnschulz said:**
> 
once the image is transfered what is the simplest way to increase the size of the partition? or will dd "just do it"?

Nope; "dd" will only create an exact replica, including the existing partition tables. You will have to manually resize the filesystems.

If you do not want to (or cannot) use gparted, you can use the manual resizing tool resize2fs.

However, I heartily recommend gparted; if you do not have a GUI environment, you can run it off a live CD/USB.

You can also use partimage (also discussed in the thread); but in this case, you will have to manually create the target partitions before restoring the image created by partimage. The target partitions can be the SAME OR GREATER SIZE than the original partition.

---

### Post by cnschulz on 2009-07-14
thank you all very much for your help.

i will go the dd / gparted boot cd path and report back.

:)

---

### Post by prshah on 2009-07-14
> **cnschulz said:**
> 
i will go the dd / gparted boot cd path and report back.

Note that having swap is good if you are using gparted. If your swap is not on an extended partition (ie, sdx1-3) then you should enable swap before using gparted. You can do this while gparted is running by right-clicking the swap partition and choosing "Swapon". If it is greyed out, don't bother. If, after enabling swap, some other partitions that you need to resize acquire a "keys" icon next to them, then you cannot resize them without turning off swap.

To turn off swap, right click the swap partition in gparted and choose "Swapoff"

---

