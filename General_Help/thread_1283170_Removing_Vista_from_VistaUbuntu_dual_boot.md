---
title: "Removing Vista from Vista/Ubuntu dual boot"
date: 2009-10-05
forum: General Help
---

### Post by jolindbe on 2009-10-05
Hi!

I've had Vista and Ubuntu installed on a dual boot (Vista installed first) for some time now, and I've realised that I'm using Vista less and less.
To reclaim some space, I am now prepared to completely remove Vista from my system. When I try to find a good guide for this (I don't want to mess up my functioning Ubuntu), I only find guides for removing Ubuntu from a Vista/Ubuntu dual boot, none for removing Vista... (strange)

Could someone help me with a general outline (or even better, a step-by-step guide)  on what I should do? To clarify, my Windows partition is "to the left", and I'd like to give that space to Ubuntu. I've heard that it might be a good idea to put the /home folder on a separate partition - would this be a good occasion of doing this move as well?

The result of running sudo fdisk -l is shown below. Sorry 'bout the Swedish, I hope that most things are obvious - let me know if there is anything in particular that needs to be translated.

```
Disk /dev/sda: 120,0 GB, 120034123776 byte
255 huvuden, 63 sektorer/spår, 14593 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x30000000

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1               1          15      120456   de  Dell-verktyg
/dev/sda2              16         277     2097152    7  HPFS/NTFS
Partition 2 slutar inte på cylindergräns.
/dev/sda3   *         277       12426    97593340    7  HPFS/NTFS
/dev/sda4           12427       14593    17406427+   5  Utökad
/dev/sda5           12427       14293    14996646   83  Linux
/dev/sda6           14294       14593     2409718+  82  Linux växling / Solaris

```

Thanks for any help!

---

### Post by PacSci on 2009-10-05
I did something pretty much exactly like this in March. The thread I started is at [http://ubuntuforums.org/showthread.php?t=1096421](http://ubuntuforums.org/showthread.php?t=1096421). Near the end is a step-by-step guide - it should tell you how to do this.

I decided not to move my /home to a separate partition - too many potential headaches. Instead, I created a partition /stor for music, photos, ISOs, backups and the like.

Also, I do think it's funny that there's nothing about removing Vista. I mean, I'd certainly want to. :-)

---

### Post by jolindbe on 2009-10-09
As my Vista partition is the active, and as the Vista bootloader loads first (after choosing Ubuntu at this menu, grub loads), don't I need to remove the Vista bootloader first? How do I do that?

---

### Post by oldfred on 2009-10-09
What boot loader are you using?

Normally Grub comes up first and then you choose Ubuntu or windows. Your partitions do not look like a Wubi install. I did not think you could use a windows boot to directly get to Ubuntu.

---

### Post by jolindbe on 2009-10-09
> **oldfred said:**
> What boot loader are you using?

Normally Grub comes up first and then you choose Ubuntu or windows. Your partitions do not look like a Wubi install. I did not think you could use a windows boot to directly get to Ubuntu.

I use Windows Vista bootloader, together with something called NeoSmart for the Ubuntu choice, which starts the Ubuntu bootloader (grub).

---

### Post by jolindbe on 2009-10-09
I followed this guide to change into Windows Vista bootloader: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

Do I need to uninstall the Vista bootloader before I start with the repartitioning?

---

### Post by oldfred on 2009-10-09
If you are going to be 100% Ubuntu you should install grub to the MBR as that is the standard, you can still boot windows but would have to add a windows stanza to menu.lst.

If you can get into Ubuntu you can do the easy way. Many of the instruction are for using a liveCD which requires mounting your system, etc. Instructions are the same as recovering from a windows install:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
#reset grub boot
sudo grub
find /boot/grub/stage1   #you will get a response such as root (hd1,0)
root (hd1,0)                 #use the numbers from the previous command
setup (hd0)

If you totally delete the partition you may renumber partitions and have issues booting. I would reformat it and use it for data.

---

### Post by jolindbe on 2009-10-10
Everything worked fine! Thanks for the help.
I just removed the Windows partition, made sure to reinstall grub on sda, selecting sda5 as the boot partition, and everything works like a charm.

Moving/expanding the partition to the left took much less time than I expected - a little less than an hour (but then it's only 12 GB or so).

---

### Post by K_REY_C on 2009-10-30
I'm wanting to remove Vista completely. I'm fairly certain I'm using the grub bootloader... but it seems to be associated with the main Vista partition (sda3). 

I'm not entirely sure how to read the output below... but will my computer still boot into Ubuntu if I reformat sda1, sda2, & sda3 as ext3 for additional storage space? 

What do I need to do to make sure my computer will still work and be Vista free?

Thanks much! fdisk -l below.

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13        1318    10485760    7  HPFS/NTFS
/dev/sda3   *        1318       19774   148249863    7  HPFS/NTFS
/dev/sda4           19775       38914   153735170+   f  W95 Ext'd (LBA)
/dev/sda5           38587       38914     2620416   dd  Unknown
/dev/sda6           19775       37818   144938398+  83  Linux
/dev/sda7           37819       38586     6168928+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89670caa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19929   160079661    7  HPFS/NTFS

```

---

### Post by jolindbe on 2009-10-30
Start up using an Ubuntu live CD. Use gparted to do whatever you want to do to your Windows partitions.
Before quitting gparted, you have to flag your Ubuntu drive as the boot drive (it should be marked by a * in the boot column above, now one of your Windows drives is the boot drive).
Before restarting, you will need to reinstall GRUB. You can e.g. use these instructions: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

