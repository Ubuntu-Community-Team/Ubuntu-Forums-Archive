---
title: "Grub Boot Menu Issue"
date: 2010-01-03
forum: General Help
---

### Post by SafariAl on 2010-01-03
I bought my laptop with Vista pre-installed, and eventually partitioned off some space to dual-boot linux. I then proceeded to also partition off more space to install windows xp. I decided that Vista was wasting space, so I deleted the partition. I didn't take into account that the grub boot menu loaded Vista, which then prompted me to choose between Vista and XP. Now it just tells me (when loading the "Vista" option from the boot menu) that there is no partition found. This makes perfect sense, but I have no clue what I should do editing-wise in the menu.lst to get it to load the XP partition.

Help is much appreciated
Thanks

---

### Post by audiomick on 2010-01-03
hallo.
You have to make the boot loader go and have another look at what systems are installed.

If you a 9.10 that was a fresh install, it will be grub2
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Anything before that, and a 9.10 that was updated from a previous version, will have grub legacy.
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by SecretCode on 2010-01-03
Post your menu.lst [assuming you have one] and the output of *sudo fdisk -l*

You may have to use Windows XP in recovery mode, as even if we set up grub properly, XP may have installed relying on some files in the Vista partition.

---

### Post by DeMus on 2010-01-03
> **SafariAl said:**
> I bought my laptop with Vista pre-installed, and eventually partitioned off some space to dual-boot linux. I then proceeded to also partition off more space to install windows xp. I decided that Vista was wasting space, so I deleted the partition. I didn't take into account that the grub boot menu loaded Vista, which then prompted me to choose between Vista and XP. Now it just tells me (when loading the "Vista" option from the boot menu) that there is no partition found. This makes perfect sense, but I have no clue what I should do editing-wise in the menu.lst to get it to load the XP partition.

Help is much appreciated
Thanks

Since all of this happened recently I would suggest to start allover with the installation of XP on approximately half the disk size, followed by the installation of Ubuntu on the other half including Grub which will recognize XP to make a perfect dual boot. You won't have any problems with Vista that way.

---

### Post by SafariAl on 2010-01-03
I'm probably going to have to re-install XP, but that's not necessarily a big deal. Most of my files were on an external HD. 

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc202b441

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        8982       10183     9655065    7  HPFS/NTFS
/dev/sda3           13731       14593     6932047+   7  HPFS/NTFS
/dev/sda4           10184       13730    28491277+   f  W95 Ext'd (LBA)
/dev/sda5           10184       13578    27270306   83  Linux
/dev/sda6           13579       13730     1220908+  82  Linux swap / Solaris

Partition table entries are not in disk order

menu.lst:

[http://pastie.org/765216](http://pastie.org/765216)

(Had some earlier issues with the ubuntu entry duplicating itself, that's why it's so long)

Any other ideas before I reinstall XP?

---

### Post by SecretCode on 2010-01-03
There's no sda1 - I presume that's where Vista was.
But you still have two NTFS partitions sda2 and sda3 - is that right? Is sda3 a data-only partition?

One more piece of data: post the output of boot_info_script - see here: [[SOLVED] Boot Info Script: How to - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by SafariAl on 2010-01-03
I'm not quite sure what sda3 is. Maybe Ubuntu recovery? I was thinking of reinstalling both OS's anyway. Ubuntu has had a few weird issues (flash, installation issues). All of it can be resolved, but it would probably be easier to reinstall. Here's all the data from the boot info thing:

[http://pastie.org/765448](http://pastie.org/765448)

---

### Post by Leppie on 2010-01-03
i think that all that was needed was re-installing the bootloader for xp using an xp recovery disc.

---

### Post by SecretCode on 2010-01-04
> **SafariAl said:**
> I'm not quite sure what sda3 is. Maybe Ubuntu recovery?Vista recovery, looking at your boot info. (You may as well delete that partition too. After everything else is working.)

---

### Post by SecretCode on 2010-01-04
> **Leppie said:**
> i think that all that was needed was re-installing the bootloader for xp using an xp recovery disc.

That should work.

---

