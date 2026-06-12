---
title: "Grub, menu.lst missing lines"
date: 2009-09-20
forum: General Help
---

### Post by evarist on 2009-09-20
So so so stupid. Dual boot XP/Ubuntu 9.07, on hd0 en hd1 respectively.
XP long since broken, only use Ubuntu. Wanted to adjust the startup screen to only show what I needed (latest version of Ubuntu only), so in Startup Manager I set the number of lines to "1", but I completely forgot about the memtest thing, so now that's the only thing (besides XP) that shows up on the list of OS's. Found a 6.07 LiveCD, so I tried something along the lines of [this]("http://www.linuxquestions.org/questions/linux-newbie-8/deleting-the-bootloader-config-file-605238/#post2983437") and [this]("http://maratux.blogspot.com/2009/03/oops-removed-all-kernels.html"), no go. 

Notes:
- Could it be that Ubuntu and the startup partition are different? Startup partition got lost, so Ubuntu is lost too?
- Also, long time ago it used to be that XP was the one starting up first, but I don't remember how or where I changed that.
- Gparted says the XP-partition (ntfs) is flagged as boot, does this contradict my previous remark?
- Gparted shows two other partitions, both of which it doesn't recognize.
- This would be sort of a "Plan C of last resort", but I'm thinking about installing the 6.07 LiveCD on the Windows partition, then upgrade to 9.07, and see if it recognizes the other partitions.

I already stepped way out of my expertise here, so I thought I'd ask you guys for help before I'm really botching things up, if I already haven't. Any help much appreciated, and thanks much for your time.

```
grub> geometry (hd1,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is fat, partition type 0xc
   Partition num: 2,  Filesystem type is fat, partition type 0xc
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 8,  Filesystem type unknown, partition type 0x82
``````
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       17458   140231353+   7  HPFS/NTFS
/dev/hda2           17459       19738    18314100    7  HPFS/NTFS
/dev/hda3           19739       19929     1534207+   b  W95 FAT32

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1963    15767766    7  HPFS/NTFS
/dev/hdb2            1964        3926    15767797+   c  W95 FAT32 (LBA)
/dev/hdb3            3927        4122     1574370    c  W95 FAT32 (LBA)
/dev/hdb4            4123       19457   123178387+   f  W95 Ext'd (LBA)
/dev/hdb5            4123        5742    13012618+   7  HPFS/NTFS
/dev/hdb6           16871       19165    18434556    7  HPFS/NTFS
/dev/hdb7           19166       19457     2345458+   7  HPFS/NTFS
/dev/hdb8   *        5743       16492    86349343+  83  Linux
/dev/hdb9           16493       16870     3036253+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

---

### Post by Woody1987 on 2009-09-20
You can just manually adjust it by typing in sudo gedit /boot/grub/menu.lst and changing it to your liking.

---

### Post by raymondh on 2009-09-20
why not just redo in SUM? (Am thinking that you still can boot into ubuntu).

---

### Post by Darkwing-Duck on 2009-09-23
Another option is use this to update the menu.list and fix your MBR.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by mike555 on 2009-09-23
or just try a different boot manager like " GAG" from ; [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by DrMelon on 2009-09-23
The PLoP bootmanager is really good too.

---

