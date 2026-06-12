---
title: "Windows XP/Ubuntu dual boot"
date: 2012-01-10
forum: General Help
---

### Post by girish53 on 2012-01-10
I have a 2006 Dell Dimension 9200 which came preinstalled with Windows XP. In 2009, my son, unbeknownst to me, installed Ubuntu on it and subsequently upgraded grub to grub 2 (I think). The bottom line is that I cannot boot Windows XP on it. On power up it shows me the following options:
1. Chainload Windows XP
2. Ubuntu ....
3. Ubuntu ....
4. Memory test ...
5. Memory test ...
6. Dell Utility partition
If I pick the first option, it says 'unknown command 'chainloader +1'.
It starts ubuntu without any problem.
How can I fix it so that I can boot Windows XP? I am not an expert in ubuntu, and my son does not know it enough either to fix it. I am also new to the forum. If this is not the right subgroup, please forward it to the right subgroup. Also, please send me an email with the instructions.
Thank you for you help.
Girish

---

### Post by lukeiamyourfather on 2012-01-10
While in Linux can you run this command and post the output? It will list all of the disks/partitions and their type. The purpose is to see if the Windows XP partition is still there or not.

```
sudo fdisk -l
```

If the Windows XP partition is still there (probably NTFS type) then updating GRUB should fix the issue. To update GRUB run the command below (and restart when it completes). It will look at the installed operating systems and kernels and rebuild the menu from scratch.

```
sudo update-grub
```

If the Windows XP partition isn't there anymore that's another story, in which case hopefully you have a Windows XP install disc or a factory recovery disc around somewhere.

---

### Post by girish53 on 2012-01-14
Here is the output of fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           7       56196   de  Dell Utility
/dev/sda2               8       18001   144530433    5  Extended
/dev/sda3           19037       19452     3341520   db  CP/M / CTOS / ...
/dev/sda5               8        3898    31249408   83  Linux
/dev/sda6            3898        4627     5858304   82  Linux swap / Solaris
/dev/sda7            4627       18001   107420672    b  W95 FAT32

Sorry for the late reply. I get time to work on my hobby machine only on the week end. Hope you are able to help me.
Thanks much.
Girish

---

### Post by oldfred on 2012-01-14
Not looking good.

Windows XP was usually in NTFS by 2006. Early versions might be FAT32. But the only Windows partition you have is sda7, FAT32 and Windows cannot boot (on its own) from a logical partition. The sda1 with the boot flag which is the partition Windows tried to boot seems to be just the Dell Utility. Not sure what sda3 is as that may be a partition with corruption of some type as the cp/m is for very old systems. Can you mount sda1, sda7 or sda3 in Ubuntu?

Do you have these files in any partition:
Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM

---

### Post by girish53 on 2012-01-18
I tried 
sudo mount /dev/sda1 /mnt/xxx

I got
mount: mount point /mnt/xxx does not exist

It did the same for sda3 and sda7.

I did
sudo find / -name WinXP -print

It did not find anything. I repeated for all the files you mentioned, in the same case as you indicated and it did not find anything.

Is it possible to boot the machine using a bootable Windows2000 flash drive or CD? Will it able to find the FAT 32 partition. As long as I can run the machine under Windows2000, I will be happy. I have Reinstallation CD and Resource CD that came with the machine. Can I use them in any way? Is there any way to install windows and not loose my work stuff on the hard drive? 

Thanks for your help.
Girish

---

### Post by nothingspecial on 2012-01-18
Moved to General Help.

---

### Post by Mark Phelps on 2012-01-18
What Ubuntu version are you running?

You should be able to find a Places menu item (in older Ubuntu versions), and under there, a list of partitions on your drive.  Clicking each of them in turn should open a Nautilus window for each.  That will automatically mount each partition for you and allow you to see the contents.

Also, since you claim to have Windows XP install media, you could do a Repair Install -- which will reinstall XP but leave your apps and data intact.  Link below has some details about that:

[http://www.michaelstevenstech.com/XPrepairinstall.htm]("http://www.michaelstevenstech.com/XPrepairinstall.htm")

---

### Post by xyzzyman on 2012-01-18
SDA3 is his recovery partition. It was very well hidden because of they way they changed the partition type even though it's a fat32 file system and hard to access once Dell's bootloader was wiped. It basically contains an autoexec.bat, Norton Ghost and a compressed image.

[http://www.goodells.net/dellrestore/fixes.shtml](http://www.goodells.net/dellrestore/fixes.shtml)

I've used the ISO burned to a CD and restored dozens of mid 2000's DELL's. This situation is harder as you'd need to delete and move some partitions. And XP Media Center 2005 always came as NTFS as it was an OEM only edition, and it was a requirement as Media Center had its DVR functionality and needed to be able to save larger file sizes if needed. If you have the original disks you really are best off just starting from scratch with Windows, as then you won't be installing all the pre-installed junkware from Dell. If you have a thumb drive around, go to dell.com, type in your service code and download the latest drivers for all your hardware and use those instead of installing them from the CD's.

As far as your data, if it's anywhere's the one place it would be is sda7, but I have a feeling your data isn't there.

---

### Post by girish53 on 2012-01-18
> **Mark Phelps said:**
> What Ubuntu version are you running?

You should be able to find a Places menu item (in older Ubuntu versions), and under there, a list of partitions on your drive.  Clicking each of them in turn should open a Nautilus window for each.  That will automatically mount each partition for you and allow you to see the contents.

Also, since you claim to have Windows XP install media, you could do a Repair Install -- which will reinstall XP but leave your apps and data intact.  Link below has some details about that:

[http://www.michaelstevenstech.com/XPrepairinstall.htm]("http://www.michaelstevenstech.com/XPrepairinstall.htm")
I have Ubuntu 10.04 LTS

---

### Post by girish53 on 2012-01-18
> **Mark Phelps said:**
> What Ubuntu version are you running?

You should be able to find a Places menu item (in older Ubuntu versions), and under there, a list of partitions on your drive.  Clicking each of them in turn should open a Nautilus window for each.  That will automatically mount each partition for you and allow you to see the contents.

Also, since you claim to have Windows XP install media, you could do a Repair Install -- which will reinstall XP but leave your apps and data intact.  Link below has some details about that:

[http://www.michaelstevenstech.com/XPrepairinstall.htm]("http://www.michaelstevenstech.com/XPrepairinstall.htm")
I do have places menu, but could not figure out how to get the list of partitions. Please let me know.

---

### Post by oldfred on 2012-01-18
If you are not mounting partitions they will be in the left column. Sometimes as the labels (I like to label my partitions), or as just the size like 220GB.

You can label with gparted when you create a partition or with Disk Utility.

---

