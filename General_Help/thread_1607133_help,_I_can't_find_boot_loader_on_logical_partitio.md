---
title: "help, I can't find boot loader on logical partition"
date: 2010-10-27
forum: General Help
---

### Post by wild_tiger on 2010-10-27
My disk partitions are as following:
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58b258b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        7296    43246980    f  W95 Ext'd (LBA)
/dev/sda5            1913        4462    20482843+   b  W95 FAT32
/dev/sda6            4463        4705     1951866    b  W95 FAT32
/dev/sda7            4706        7174    19832211   83  Linux
/dev/sda8            7175        7296      979933+  82  Linux swap / Solaris

There already exist an os XP before my installing of ubuntu.When I installed my ubuntu 9.10, I selected to install grub2 on the logical partition sda7. But when I typed command sudo dd if=/dev/sda7 of=mbr bs=512 count=1, I found that
the file mbr was eerily full of zero bytes. How does this happen?  Or grub2 can't be installed on a logical partition? But it works very well along with win7 rather than XP.

---

### Post by WorMzy on 2010-10-27
Your bootloader is installed to /dev/sda1 (hence the bootflag in the fdisk output), only stage1 of grub is installed to the MBR, the rest is installed -inside- your Ubuntu partition's /boot folder.

I'm not familiar with dd or it's commands, but what is it you're trying to do?

---

### Post by Quackers on 2010-10-27
grub2 should be installed to the MBR of sda (not sda7)
I've never used the dd command but how I read it you are trying to copy the contents of /dev/sda7 to mbr. 
Is this in an attempt to put grub in the MBR of sda, having realised your mistake?

---

### Post by oldfred on 2010-10-27
Grub2 does not like to install to a partition (PBR) as it is less reliable. It has to use blocklists which are hard coded addresses for the files. If any file gets moved due to updates or even file checks you then have to reinstall.

Normally you install grub to the MBR of the drive. Grub will then give you a choice to boot either Ubuntu or XP. 

I think I have seen instructions somewhere on trying to use the windows boot loader and editing boot.ini to use the saved grub file from the dd command. I do not recommend that because of the block list issue. Just use grub2.

---

### Post by wild_tiger on 2010-10-28
Thanks for all of your enthusiastic replies. Just as 3rd floor said, I do really want to use the xp's boot loader and the saved grub file from the dd command to boot my ubuntu. I know it is not recommended to do so as it is less reliable. I just want to know why it didn't work. I have seen some tutorial on the web said that I can install the grub on a logical partition where ubuntu will be installed instead of on the mbr. And I have made win7's boot loader to load the saved grub2 file successfully, which also is installed on a logical partition. What's the reason of the difference? Might the reason is grub2 can't be installed on a logical partition,  and the tutorial found on the web is wrong?

---

### Post by oldfred on 2010-10-28
When grub2 first came out I used grub legacy to chainboot everything. I installed grub2 to a logical partition then. I do not know why it would not work now.

How did you try to install grub2. I think the manual install lets you choose partitions without question, but if reinstalling you have to use --force.

---

### Post by wild_tiger on 2010-11-02
I used --forece, but it didn't help.

---

### Post by alphaamanitin on 2010-11-02
> **wild_tiger said:**
> My disk partitions are as following:
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58b258b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda2            1913        7296    43246980    f  W95 Ext'd (LBA)
/dev/sda5            1913        4462    20482843+   b  W95 FAT32
/dev/sda6            4463        4705     1951866    b  W95 FAT32
/dev/sda7            4706        7174    19832211   83  Linux
/dev/sda8            7175        7296      979933+  82  Linux swap / Solaris

sudo dd if=/dev/sda7 of=mbr bs=512 count=1, I found that
the file mbr was eerily full of zero bytes. 

The only thing I can say is that your dd command looks wonky.  if=/dev/sda7 of=mbr so the input file is /dev/sda7 and the output file is mbr, but mbr of what?  Now I am not really sure about all the uses of the dd command so maybe you have done it right and I just don't know it, but I don't understand how the computer would know where to write the output.  I can only assume that it writes the output to the current working device, which may or may not be where you want it.  Please explain this to me if I am wrong, I would like to learn more about dd.
[COLOR=Red][B]
Ah I just noticed you only have the one device, /dev/sda.  Nevermind then.[/B][/COLOR]

AlphaA

---

### Post by wild_tiger on 2010-11-02
Mbr is just a file name which can be another if you will. And it is writed to your current work folder. Since my current work folder when I typed the dd command was home folder, mbr was writed to home.

---

### Post by alphaamanitin on 2010-11-03
> **wild_tiger said:**
> Mbr is just a file name which can be another if you will. And it is writed to your current work folder. Since my current work folder when I typed the dd command was home folder, mbr was writed to home.


Yeah I noticed that and added it to my post.  I thought you were trying to copy the MBR to another device.  My mistake.

AlphaA

---

