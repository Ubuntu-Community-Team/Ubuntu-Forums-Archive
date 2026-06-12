---
title: "VirtualBox - Running Existing Vista on Ubuntu Problem"
date: 2009-10-18
forum: General Help
---

### Post by p4ddym on 2009-10-18
I want to run Vista through Virtual Box on Ubuntu. Vista is already installed on one hard disk. Ubuntu on another.
Fdisk-1 looks like this
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       30394   233580544    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf275e3de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29643   238107366   83  Linux
/dev/sdb2           29644       30394     6032407+   5  Extended
/dev/sdb5           29644       30394     6032376   82  Linux swap / Solaris

```I have followed these instructions ([http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)).
I managed to get it to start the windows loader it got me to choose Windows Vista from the list. When I press enter to choose Vista it just restarts the VM and asks me to choose again. I have also had a different scenario where it produced a grub loader error 21. 
What can I do to fix this and be able to boot vista without any hiccups?

Thanks...

---

### Post by yanceypd on 2009-10-18
Did you do a complete Vista install into VM?  I think you have to do a real install there.  I did this one time, ran but was very slow. Boot to separate drives 1 Vista 1 Ubuntu.

---

### Post by p4ddym on 2009-10-18
> **yanceypd said:**
> Did you do a complete Vista install into VM?  I think you have to do a real install there.  I did this one time, ran but was very slow. Boot to separate drives 1 Vista 1 Ubuntu.

No. Vista was already installed. I am trying to boot it through VM

---

