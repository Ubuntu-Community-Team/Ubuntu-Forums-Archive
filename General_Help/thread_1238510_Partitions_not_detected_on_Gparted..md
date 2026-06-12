---
title: "Partitions not detected on Gparted."
date: 2009-08-12
forum: General Help
---

### Post by anchorschmidt on 2009-08-12
I tried to triple boot with Ubuntu 9.04 (ext4), Mandriva and Windows 7. Ubuntu and Windows 7 were already installed but I had a problem with the installation and I found that there was no grub left and when I booted into the Ubuntu live cd to check the partitions. There weren't any partitions being recognized. I still have my data as I can mount them like volumes but they are not shown in the partition table. How can I have them recognized as partitions again? Please help.

---

### Post by rajeev1204 on 2009-08-12
Go to system>administration>partition editor then start it.It should list the partitions.

Happens sometimes .

---

### Post by anchorschmidt on 2009-08-12
The entire thing is blank. Unallocated Space.

---

### Post by michy99 on 2009-08-12
What do you get for```
sudo fdisk -l
```You might try testdisk to recover the partition table.

---

### Post by anchorschmidt on 2009-08-12
Here's the output

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000013a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7908    63520978+  83  Linux
/dev/sda2            7909       11964    32579820   83  Linux
/dev/sda3   *       12518       19107    52934175    7  HPFS/NTFS
/dev/sda4           11965       19457    60187522+   f  W95 Ext'd (LBA)
/dev/sda5           11965       12244     2249068+  83  Linux
/dev/sda6           19108       19457     2811343+  82  Linux swap / Solaris
/dev/sda7           12245       12284      321268+  82  Linux swap / Solaris
/dev/sda8           12285       12517     1871541   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a7542

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         977     7847721    c  W95 FAT32 (LBA)
```

How do I run testdisk?

---

### Post by michy99 on 2009-08-12
fdisk seems to see your partitions fine. Are you sure you have the right disk selected in gParted? (A screenshot might help.)

To run testdisk, you have to install it first.```
sudo apt-get install testdisk
```

---

### Post by anchorschmidt on 2009-08-12
Here's the screenshot. I tried to run the command but testdisk wasn't in the repos, nor could I find it in Synaptic. I'll try to find it somewhere.

---

### Post by michy99 on 2009-08-12
Testdisk shows as being available in the universe repository on my system. Are you running a 64-bit system by any chance? You can also get it from:

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by P4man on 2009-08-12
woha.. thats ahm.. odd.

Before running testdisk, perhaps your partitions are fine, but this is a gparted issue? If you select sdb in gparted does that show normally?

---

### Post by anchorschmidt on 2009-08-12
I got it, but how do I use it?

---

### Post by P4man on 2009-08-12
Here is a bug report that should interest you:
[https://bugs.launchpad.net/ubuntu/+source/parted/+bug/96976](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/96976)

from that thread, try running the command line version:

```
sudo parted
print

```

(quit to quit)

paste the results here. wondering if you get the same "It is not possible to have partition outside the disk.".

Im not sure if this is really a bug in (g)parted, or a real problem with your partition table.

---

### Post by anchorschmidt on 2009-08-12
if I select sdb then I get this. It's just my USB stick but I'll upload a screenshot, if it provides you with any info.

---

### Post by michy99 on 2009-08-12
I hae never used testdisk myself, but you start it from the command line with```
sudo testdisk
```See if there is an option to repair the partition table, or scan for partitions, or something of that nature. But you might want to try P4man's suggestion first.

---

### Post by anchorschmidt on 2009-08-12
OK guys, thanks to the amazing help you all have been giving me I am starting to realize what's wrong with my system. It so happens that two of the partitions are overlapping because of which Gparted is showing an unallocated disk. I'll try with qtparted to see if the same thing keeps happening.

---

### Post by michy99 on 2009-08-12
Now that I look at the output from fdisk, I see that sda3 is inside sda4. Now, sda4 is an extended partition, so it  is supposed to have logical partitions inside, which sda5, 6, 7, and 8 are. But logical partitions start at sda5 so sda3 should not be a logical partition. Having seen the problem, I'm afraid someone more knowledgable than I will have to tell you how to fix it.

---

