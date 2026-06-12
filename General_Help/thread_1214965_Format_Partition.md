---
title: "Format Partition"
date: 2009-07-16
forum: General Help
---

### Post by theumang on 2009-07-16
Hi,

I have a 250gb (sata) hd, used as follows :
15 gb : ext4 partition - root
5 gb : swap space
The rest is free, did not format when installed.

Now I want to use that space & I do not find gparted on ubuntu anymore, it was there on 7.04, Right? Anyways what do we do here ?

Thanx
Umamg

---

### Post by philinux on 2009-07-16
gparted is in my repo. You need to use the livcd to do what you want.

```
sudo apt-get install gparted
```

---

### Post by Ra-Hoor-Khuit on 2009-07-16
It's still there but it's been relabeled "Partition Manager" if memory serves me correct.  If you want to manage your existing partitions however, you'll need the LiveCD of **gParted** (now called PartedMagic) since you can't "work" (e.g resize) a mounted partition.

---

### Post by raymondh on 2009-07-16
> **Ra-Hoor-Khuit said:**
> It's still there but it's been relabeled "Partition Manager" if memory serves me correct.  If you want to manage your existing partitions however, you'll need the LiveCD of **gParted** (now called PartedMagic) since you can't "work" (e.g resize) a mounted partition.

and when you do use the liveCD, just to be sure everythin is indeed unmounted, right click on all the partitions and if you are given the option to unmount, do so.  For swap, use swapoff.

I know, I know :)  'Better to be sure that they are indeed unmounted.

---

### Post by theumang on 2009-07-17
The space that I want to use is the Free space, its not even formatted.
I don't think I'll need the Live CD in that case, will I ?
I don't know where to find it on the Live cd too.

---

### Post by philinux on 2009-07-17
> **theumang said:**
> The space that I want to use is the Free space, its not even formatted.
I don't think I'll need the Live CD in that case, will I ?
I don't know where to find it on the Live cd too.

In that case use info in post #2. I guess gparted will appear in the system>admin menu.

---

### Post by az on 2009-07-17
> **theumang said:**
> The space that I want to use is the Free space, its not even formatted.
I don't think I'll need the Live CD in that case, will I ?
I don't know where to find it on the Live cd too.

It's best to unmount every partition on the drive you want to partition.  So, yes, you should use a live cd.  Whether it's the Ubuntu Live cd or another one...

---

### Post by theumang on 2009-07-18
> umang@ubuntu:~$ sudo apt-get install gparted
[sudo] password for umang: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mozilla-plugin-gnash (0.8.5-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing mozilla-plugin-gnash (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 mozilla-plugin-gnash
E: Sub-process /usr/bin/dpkg returned an error code (1)

This error is being worked upon on [here]("http://ubuntuforums.org/showthread.php?t=1213705")

---

