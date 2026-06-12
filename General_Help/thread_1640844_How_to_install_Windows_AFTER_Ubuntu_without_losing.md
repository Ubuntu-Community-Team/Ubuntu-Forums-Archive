---
title: "How to install Windows AFTER Ubuntu without losing it?"
date: 2010-12-08
forum: General Help
---

### Post by micael3000 on 2010-12-08
Hello,

I would like to know how can I install Windows XP on my laptop, after Ubuntu, without losing it. I want a dual boot on windows and ubuntu...

I am using ubuntu 10.10 and I have 4 partitions on my HardDisk, I don't know what are the primary partitions...

Thanks in advance!

---

### Post by Spyderkid on 2010-12-08
install ubuntu **_don't use the whole disk_** then when you insert the windows CD its asks where you want to install it, install it in the [B]non-partitioned space.
[/B]


*Easy as Pie!*

---

### Post by micael3000 on 2010-12-08
But after that Windows will always boot without Grub asking me what OS i want to go for... How to fix it?

---

### Post by azertyh on 2010-12-08
hello,
read the [doc about it](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).

---

### Post by coffeecat on 2010-12-08
[Re-installing grub 2 after installing Windows.]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by ean5533 on 2010-12-08
[How to install Windows after Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing Windows After Ubuntu")

---

### Post by sikander3786 on 2010-12-08
Windows needs a primary partition to boot from. Can you manage to give it a primary partition?

Please post the output of this command from Applications > Accessories > Terminal.

```
sudo fdisk -l
```

It would give us an idea of your partitions.

And Windows will definitely over-ride Grub in your MBR and you'll need to re-install it afterwards. See here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Just 2 commands and you are done.

If you don't feel confident, feel free to post back ;-)

---

### Post by micael3000 on 2010-12-08
Thats the output:
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf90751e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24899   199999488   83  Linux
/dev/sda2           24900       60802   288384001    5  Extended
/dev/sda5           24900       49798   199999488    b  W95 FAT32
/dev/sda6           49798       51043     9999360   82  Linux swap / Solaris
/dev/sda7           51043       60802    78383104   83  Linux

I am not confident yet haha fear of losing all my stuff because of this damn OS :)

---

### Post by oldfred on 2010-12-08
Partitions do not have to be in order. You can shrink sda1, if it is not full of data and create sda3 in the free space. Format it as NTFS and move boot flag to sda3 while in gparted. Primary partition are sda1 thru sda4. 

Of course you should have good backups anytime you modify partitions.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

### Post by micael3000 on 2010-12-22
Thanks for helping! =D

---

### Post by micael3000 on 2011-08-07
Just updating... This weekend we did it at a friend's laptop and it is VERY easy... Just install windows in a free partition and then boot a livecd with ubuntu (or any other operation system), mount the linux partition anywhere (/mnt for instance) and then run grub-install on it.

Pretty simple, 3 commands solve the problem.

---

