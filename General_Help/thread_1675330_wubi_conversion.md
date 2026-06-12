---
title: "wubi conversion?"
date: 2011-01-25
forum: General Help
---

### Post by george-test on 2011-01-25
Good day all

I recently installed Ubuntu 10.10 64 bit on my Dell laptop using wubi. Ubuntu now shares the drive win 7 64 bit. I installed my ATI propriety drivers without a hitch. But I am holding off installing any of the other updates. The main reason for this is the fact that I read that some updates could render a wubi ubuntu installation boot less.

As there is information and programs I need to access daily on the win 7 installation I cannot take a change so please any advice should be ‘known to definitely have worked’ please &#9786; I would like to convert the wubi installation to a permanent partition without losing any info on either installs. Is this possible?*

Thanks in advance

---

### Post by DanneStrat on 2011-01-25
> **george-test said:**
> Good day all

I recently installed Ubuntu 10.10 64 bit on my Dell laptop using wubi. Ubuntu now shares the drive win 7 64 bit. I installed my ATI propriety drivers without a hitch. But I am holding off installing any of the other updates. The main reason for this is the fact that I read that some updates could render a wubi ubuntu installation boot less.

As there is information and programs I need to access daily on the win 7 installation I cannot take a change so please any advice should be ‘known to definitely have worked’ please &#9786; I would like to convert the wubi installation to a permanent partition without losing any info on either installs. Is this possible?*

Thanks in advance

I've used wubi myself and I've never had an unbootable

wubi installation after updating.

Since wubi is the easiest way(I would say) to dual boot

without risking to lose any data (which can be the case when partitioning),

I would just apply those updates and reboot the machine to make sure

everything works. If it doesn't you can just boot back into windows

and reinstall ubuntu with wubi. Easy as that!

Good luck!

---

### Post by bcbc on 2011-01-25
> **george-test said:**
> Good day all

I recently installed Ubuntu 10.10 64 bit on my Dell laptop using wubi. Ubuntu now shares the drive win 7 64 bit. I installed my ATI propriety drivers without a hitch. But I am holding off installing any of the other updates. The main reason for this is the fact that I read that some updates could render a wubi ubuntu installation boot less.

As there is information and programs I need to access daily on the win 7 installation I cannot take a change so please any advice should be &#8216;known to definitely have worked&#8217; please &#9786; I would like to convert the wubi installation to a permanent partition without losing any info on either installs. Is this possible?*

Thanks in advanceFirst off, if you wubi install is important then you should back it up. Copying the root.disk (and other virtual disks if you created them e.g. home.disk (not swap.disk)) is sufficient. You can copy them back over if something goes wrong.

Second, it's the updates to grub2 (packages grub-pc and grub-common) that are breaking Wubi.

Third, yes there is a way to migrate a Wubi install to partition. You have to create the partition(s) first. Win 7 has a disk utility that can shrink the windows partition. Then you can boot Wubi, install and run GParted and create an extended partition in the space you created, and then within that two logical partitions - one for Ubuntu and one for swap. Then migrate your ubuntu using the script here:[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

NOTE: you can have a maximum of 4 primary partitions. If you already have four, then you cannot create a new extended. If you need help, give the results of (-l = small -L):
```
sudo fdisk -l
```

---

