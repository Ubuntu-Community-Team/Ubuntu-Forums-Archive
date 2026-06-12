---
title: "Can't read partition table?"
date: 2011-08-01
forum: General Help
---

### Post by goofster1020 on 2011-08-01
After reinstalling Windows on it's own partition, I went through the normal procedure to try and reinstall GRUB as my bootloader. The thing was, it thought that the whole hard drive was unallocated for some reason and I really have no clue why. I finally did get GRUB back though because I could mount the partitions from the terminal, but programs like gparted tell me I don't have anything on my HDD. Any ideas?

---

### Post by jerrrys on 2011-08-02
there is a product called testdisk, that may help or not

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by glene77is on 2011-08-02
> **goofster1020 said:**
> After reinstalling Windows on it's own partition, I went through the normal procedure to try and reinstall GRUB as my bootloader. The thing was, it thought that the whole hard drive was unallocated for some reason and I really have no clue why. I finally did get GRUB back though because I could mount the partitions from the terminal, but programs like gparted tell me I don't have anything on my HDD. Any ideas?

Have  Re-Installed Windows XP   three times, 
M$ XP always over-writes the ENTIRE hard drive.
M$ XP install procedure provides 3 warnings that this will occur!
This wipes out  my  Linux partition.     :(

---

### Post by psusi on 2011-08-02
gparted shows an empty drive whenever it finds any corruption in the partition table.  Post the output of fdisk -lu to see what's wrong with it.

---

### Post by goofster1020 on 2011-08-02
> **psusi said:**
> gparted shows an empty drive whenever it finds any corruption in the partition table.  Post the output of fdisk -lu to see what's wrong with it.

After running fdisk -lu I get this:

omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   123571979    61737795    7  HPFS/NTFS
/dev/sda3       123572104   148729769    12578833    f  W95 Ext'd (LBA)
/dev/sda4       144536868   148729769     2096451   82  Linux swap / Solaris
/dev/sda5       123572106   144536804    10482349+  83  Linux


It all looks fine to me except for where it says omitting empty partition (5) at the top but I think that's due to me using that partition currently?

---

### Post by psusi on 2011-08-02
Strange, everything does look fine except that weird error I don't understand.

What does parted -l say?

---

### Post by goofster1020 on 2011-08-02
Oh, weird.. it says "Error: Can't have overlapping partitions." How in the heck did that happen? :?

Edit: I took a look with fdisk -ul again and apparently I think my swap space and another partition are overlapping. Is there a good way to fix this?

---

### Post by psusi on 2011-08-03
It doesn't appear to be overlapping to me.

---

### Post by psusi on 2011-08-03
Oh!  Nevermind!  I didn't even notice that.. my brain kept thinking that the swap partition was a logical partition and so it was fine, but it isn't; it's a primary partition and overlapping with the extended partition.  You need to delete it and recreate it as a logical partition.

---

### Post by goofster1020 on 2011-08-03
Oh thank you :D Haha, problem solved! I'll get to that as soon as I can!

---

