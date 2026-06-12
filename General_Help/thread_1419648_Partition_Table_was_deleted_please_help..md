---
title: "Partition Table was deleted please help."
date: 2010-03-02
forum: General Help
---

### Post by jlittlemyer on 2010-03-02
I was working on creating a partition on a new hard drive I was planning on using for storage. I wasn't paying attention and chose to delete the partition on my master. I am running a dual boot with Vista and Ubuntu. When I rebooted It will only go to the Grub> prompt. Ive ran TestDisk and though that I had corrected the problem but it didnt. After running TestDisk again here is what It came up with.

Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
L HPFS - NTFS              0  32 33 28554 254 63  458734027
L Linux                28555   1  1 38585 254 63  161147952
L Linux Swap           38586   1  1 38912 254 63    5253192


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
SWAP2 version 1, 2689 MB / 2565 MiB

I pressed 'p' and checked the NTFS partition and it has my windows files.

the Linux contains the grub folder with stage1 and stage 2
EXT3 Large file Sparse superblock, 82 GB / 76 GiB

 L Linux                28555   1  1 38585 254 63  161147952
Directory /boot/grub

drwxr-xr-x     0     0      4096 12-Nov-2009 01:50 .
drwxr-xr-x     0     0      4096 19-Feb-2010 23:43 ..
-rw-r--r--     0     0        15 17-Jun-2009 04:56 device.map
-rw-r--r--     0     0       512 17-Jun-2009 04:56 stage1
-rw-r--r--     0     0    121740 17-Jun-2009 04:56 stage2
-rw-r--r--     0     0      8288 17-Jun-2009 04:56 e2fs_stage1_5
-rw-r--r--     0     0      7856 17-Jun-2009 04:56 fat_stage1_5
-rw-r--r--     0     0      8712 17-Jun-2009 04:56 jfs_stage1_5
-rw-r--r--     0     0      7352 17-Jun-2009 04:56 minix_stage1_5
-rw-r--r--     0     0      9756 17-Jun-2009 04:56 reiserfs_stage1_5
-rw-r--r--     0     0      9556 17-Jun-2009 04:56 xfs_stage1_5
-rw-r--r--     0     0       197 17-Jun-2009 04:56 default
-rw-r--r--     0     0        16 17-Jun-2009 04:56 installed-version
-rw-r--r--     0     0      4850 12-Nov-2009 01:50 menu.lst
-rw-r--r--     0     0      4850 12-Nov-2009 01:50 menu.lst~
-rw-r--r--     0     0     10510 30-Sep-2009 17:44 menu.lst.new

The linux swap parttion is as follows:
Disk /dev/sda - 320 GB / 298 GiB - CHS 38914 255 63
     Partition               Start        End    Size in sectors
L HPFS - NTFS              0  32 33 28554 254 63  458734027
L Linux                28555   1  1 38585 254 63  161147952
L Linux Swap           38586   1  1 38912 254 63    5253192


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, 
     Enter: to continue
SWAP2 version 1, 2689 MB / 2565 MiB


After hitting Enter here are the settings I came up with.
I dont know where the number 3 is coming from.

1 * HPFS - NTFS              0  32 33 28554 254 63  458734027
 2 P Linux                28555   1  1 38585 254 63  161147952
 3 E extended LBA         38586   0  1 38912 254 63    5253255
 5 L Linux Swap           38586   1  1 38912 254 63    5253192


Any Ideas would be greatly appreciated.

After writing the table above I rebooted. Windows prompted me for my restore disk. I rebooted to the live cd again and ran Fdisk.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28555   229367013+   7  HPFS/NTFS
/dev/sda2           28556       38586    80573976   83  Linux
/dev/sda3           38587       38913     2626627+   f  W95 Ext'd (LBA)
/dev/sda5           38587       38913     2626596   82  Linux swap / Solaris

---

### Post by Robster2 on 2010-03-02
Fear not

[http://www.sysresccd.org/](http://www.sysresccd.org/)

Burn the disk and boot from it.

Your problems will soon be solved!

---

### Post by jlittlemyer on 2010-03-02
Will do. I tried last night but I could not burn the iso due to having to boot via live cd. Thanks for the info.

---

### Post by jlittlemyer on 2010-03-02
Not sure if im missing the point of this cd. It has all the same utilities as Ubuntu live cd. Im fairly new to Linux so Im probably missing something there :). Im desperate for an explanation of how to get the partition table repaired.

---

