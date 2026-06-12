---
title: "GRUB does not work properly on boot"
date: 2011-03-05
forum: General Help
---

### Post by thiemnguyen on 2011-03-05
Hello everyone. :) I'm absolutely new to Linux Ubuntu. :(

Today when working with Windows 7 Disk Management, I carelessly mark the partition on which Win 7 is installed as ACTIVE and the chain of problems began. :(

When I restarted my laptop, something like this appeared:
```
No such partition.
Grub rescue>_
```

I searched around on google for hours and found a way to temporarily get back to normal boot loader by typing these commands:
// I typed "ls" and it showed me 6 partitions just from (hd0,msdos1) to (hd0,msdos6) and (hd0,msdos3) was where I found 'grub' folder

> set prefix=(hd0,msdos3)/boot/grub
set root=(hd0,msdos3)
insmod linux
normal

Then it took me the normal boot loader and I managed to enter both Linux and Win 7 but when I restarted, the 'grub rescue' appeared once again. :(

I tried to set other primary partitions as ACTIVE but nothing changed. :(

Then I entered this forum and found somewhere a similar post about GRUB error and I try these commands in my terminal right in Linux OS (not from a live CD)

> sudo grub-install /dev/sda
sudo update-grub

After rebooting this screen appeared:
> GNU GRUB    version 1.98-1ubuntu8

Minimal BASH-like line editing is supported. For the first word, TAB 
lists possible command completions. Anywhere else TAB lists possible
devices or file completions .

grub>  _

I tried using commands taken from 'GRUB rescue' error and it worked but this screen still showed whenever I start my laptop.

Here is what I'm given when I run fdisk -l
> isk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb30bf1cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              14        6350    50895872    7  HPFS/NTFS
/dev/sda3   *        6350        7647    10423296   83  Linux
/dev/sda4            7648       30400   182762578    f  W95 Ext'd (LBA)
/dev/sda5            7648       28761   169598033    7  HPFS/NTFS
/dev/sda6           30036       30400     2923520   82  Linux swap / Solaris


again, I must say that I'm totally new to Linux and I just follow these commands without understanding fully about GRUB and I don't know exactly what I have to do now to solve this problem.

Please help me, thank everyone beforehand. :D

---

### Post by TeoBigusGeekus on 2011-03-05
Follow this guide
[http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")
to reinstall grub 2.

---

### Post by thiemnguyen on 2011-03-05
Thanks for your reply. Is it compulsory to execute those commands on a live CD or I just can run them right in Linux OS?

---

