---
title: "External HD very very slow"
date: 2011-02-21
forum: General Help
---

### Post by mulanee on 2011-02-21
Hi there,
I worry about mounting properly an extaernal USB hard disk.
It is a sata 1To NTFS formatted
It works perfectly with a XP SP3.
With xuxbuntu 10.10 , with ntfs-3g installed , it is VERY long to transfer data:it took almost 3 days for 360Go.
When I connect to the station , it automatically mount by itself on /media/disk without any option;I suspect bad options are used and no use of NTFS-3G.
How to oblige it to mount with good options ?
Thank you.

---

### Post by VCoolio on 2011-02-21
Does it have a line in /etc/fstab? Else add something like (use blkid to find out label or UUID for your disk):
LABEL=addlabelhere /media/disk ntfs-3g users,rw,noauto 0 0

Maybe the option noatime helps, but I don't know if that works on ntfs, also it doesn't make THAT big of a difference. Best is to use ext4 or jfs or btrfs if you're feeling lucky, but you won't be able to use it on windows then (unless you share via network).

---

### Post by mulanee on 2011-02-22
This disk is a shuttle between different stations , it has to be in NTFS.
Modification of fstab doesn't work , after a mount -a , disk is not mounted.

---

### Post by Mark Phelps on 2011-02-22
I'm guessing you're connecting it via USB port, right?

Do you know what USB versions your PC Supports? (i.e., 1.0, 1.1, 2.0).  The version will make a lot of difference in throughput speed.

Also, look into your BIOS and see what it supports.  IF you have legacy USB support turned on (for 1.0 and 1.1) try turning it off and see if that improves throughput speed.

---

### Post by replikanxxl on 2011-12-23
""Also, look into your BIOS and see what it supports. IF you have legacy USB support turned on (for 1.0 and 1.1) try turning it off and see if that improves throughput speed.""

This definitely trippled my transfer Speed

---

