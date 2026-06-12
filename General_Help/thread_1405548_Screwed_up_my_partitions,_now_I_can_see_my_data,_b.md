---
title: "Screwed up my partitions, now I can see my data, but no boot!"
date: 2010-02-12
forum: General Help
---

### Post by Fixman on 2010-02-12
I recently made a new partition and installed Windows 7 in there. My partition table at that time was:

Ubuntu home
Windows 7
Ubuntu root
Swap memory

Of course, Windows destroyed my GRUB configuration, so I got my old Live CD, but the root partition didn't show, and gParted showed it as an unallocated partition! So I used testdisk to recover my partitions, rebooted, and now I can see all my 3 partitions, however I can't boot from then (it shows me "Missing Operating System") and gParted shows me that all the hard drive is unallocated!

Does anyone have a solution for this? testdisk reported the hard drive perfectly.

---

### Post by Muscovy on 2010-02-12
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You'll need to "replace" grub to pint back to Ubuntu. You can do this in a LiveCD.

---

### Post by VMC on 2010-02-12
> **Fixman said:**
> I recently made a new partition and installed Windows 7 in there. My partition table at that time was:

Ubuntu home
Windows 7
Ubuntu root
Swap memory

Of course, Windows destroyed my GRUB configuration, so I got my old Live CD, but the root partition didn't show, and gParted showed it as an unallocated partition! So I used testdisk to recover my partitions, rebooted, and now I can see all my 3 partitions, however I can't boot from then (it shows me "Missing Operating System") and gParted shows me that all the hard drive is unallocated!

Does anyone have a solution for this? testdisk reported the hard drive perfectly.

I don't know how you installed Windows7, but it very well may have wiped it out. 

Output the following command, from a Terminal:

```
sudo fdisk -l

```
So we can see what your partitions look like.

---

### Post by Fixman on 2010-02-12
> **VMC said:**
> I don't know how you installed Windows7, but it very well may have wiped it out. 

Output the following command, from a Terminal:

```
sudo fdisk -l

```
So we can see what your partitions look like.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19099   153412684   83  Linux
/dev/sda2           19100       19112      102400    7  HPFS/NTFS
/dev/sda3           19112       27363    66276352    7  HPFS/NTFS
/dev/sda4           27364       30402    24410767+   f  W95 Ext'd (LBA)
/dev/sda5           27364       29275    15358076   83  Linux
/dev/sda6           29276       30401     9044552   82  Linux swap / Solaris
```

sda1 is the Ubuntu home partition, sda2 is a Windows "reserved
 for the system" partition (that W7 installs automatically), sda3 is the Windows partition, sda5 is the Ubuntu root partition and sda6 is the swap memory.

---

### Post by Luisnux on 2010-02-12
Hey buddy, I did not see what version of ubuntu you're using.  However so long as you're not using Ubuntu 9.10 (Grub version 2) you can use the following tutorial that makes it very simple to rewrite Grub.  [http://www.youtube.com/watch?v=WtBBl6HvdpM](http://www.youtube.com/watch?v=WtBBl6HvdpM) 

Hope it works.

---

### Post by Fixman on 2010-02-12
> **Luisnux said:**
> Hey buddy, I did not see what version of ubuntu you're using.  However so long as you're not using Ubuntu 9.10 (Grub version 2) you can use the following tutorial that makes it very simple to rewrite Grub.  [http://www.youtube.com/watch?v=WtBBl6HvdpM](http://www.youtube.com/watch?v=WtBBl6HvdpM) 

Hope it works.

The problem here is that I have 9.10 and so GRUB 2, but for some reason I can't use the 9.10 Live CD (not when I burn it, not when I put it on an USB, and not even when I use the CD I received from Canonical). I remember having this same problem when installing 9.10, and solved it using the i915.modeset=0 option on the Live CD menu, but that doesn't seem to work not.

---

