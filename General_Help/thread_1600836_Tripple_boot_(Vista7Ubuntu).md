---
title: "Tripple boot (Vista/7/Ubuntu)"
date: 2010-10-19
forum: General Help
---

### Post by sonicj on 2010-10-19
I have vista and ubuntu already set up as a dual boot on my laptop. I got a copy of windows 7 but I've halted on installing it because while I wouldn't have a problem creating a fourth partion, I'm afraid that if install it I will lose my grub manager. The last time that happened, I couldn't manually add my ubuntu partion back to my boot list, and I had to reinstall it. 

Would that still happen? Is there a way to reinstall grub after installing 7 and have access to all 3 OSes? (I also have another partion for vista recovery.)

---

### Post by sarcasmrules on 2010-10-19
Yes this is very tricky as Windows 7 tends to override the GRUB because microsoft don't like Linux very much. I think the best thing to do is to backup your data then to reinstall Ubuntu after installing Windows 7. 
Or do what I do and have each on a separate hard drive so they boot directly from BIOS rather than GRUB:lolflag:

---

### Post by sikander3786 on 2010-10-19
You can follow this page for reinstallation of Grub.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

You'll need to add a primary partition for Windows 7 as it won't be able to boot off an extended/logical drive.

Can you please post the output of

```
sudo fdisk -l
```

so we can have a look at your current setup.

---

### Post by nads_da_man on 2010-10-19
if you have problems accessing your windows after the installation of windows over ubuntu i would suggest
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7")
good luck !

---

### Post by sonicj on 2010-10-19
Thanks for the replies guys, I'll just leave this terminal output for the user who requested it, I'm short on time and have to leave, I'll check this thread soon!

> 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfd338468

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35910   288447043+   7  HPFS/NTFS
/dev/sda2           37088       38913    14658560    7  HPFS/NTFS
/dev/sda3           35911       37088     9462142+   5  Extended
/dev/sda5           35911       36127     1743021    7  HPFS/NTFS
/dev/sda6           36128       37088     7718912   83  Linux

Partition table entries are not in disk order

Disk /dev/mmcblk0: 1030 MB, 1030225920 bytes
4 heads, 3 sectors/track, 167680 cylinders
Units = cylinders of 12 * 512 = 6144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1              21      167680     1005958+   6  FAT16


---

### Post by sikander3786 on 2010-10-19
Where are you planning to create a new partition for Windows 7?

What does sda2 contain?

---

### Post by sonicj on 2010-10-19
If I'm not mistaken, that is a small partion I use indepentent of any OS, just to store my info when I make music. As far as *where* I plan to store 7, I was going to shrink my vista partion and then create a partion from the remaining free space.

---

### Post by sikander3786 on 2010-10-19
> I was going to shrink my vista partion and then create a partion from the remaining free space.

Alright.

You can do it the way you have planned to. You will only need to install the bootloader for Ubuntu after Win 7 gets installed.

You can use the link in my above post for reinstallation of Grub.

There is also a Windows based boot loader that can boot Linux. It is called EasyBCD.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by oldfred on 2010-10-19
You need to be sure to create it as sda4, so it is a primary partition.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

to reinstall grub2.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install MBR from LiveCD, Ubuntu install on sda6 and want grub2 in drive sda's MBR:
Find linux partition, change sda6 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by sonicj on 2010-10-19
Thanks for all of the help guys, I'll tell you how it goes when I get the chance.

---

### Post by sonicj on 2010-10-22
So much for that, I was making an entire backup of my HD to an external HD, seven hours later I come back and for some reason every thing is erased. Now I'm just using win 7, I'll find time to install ubuntu on the side.

---

