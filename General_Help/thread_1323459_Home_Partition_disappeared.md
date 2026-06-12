---
title: "Home Partition disappeared"
date: 2009-11-11
forum: General Help
---

### Post by lerrup on 2009-11-11
Due to a hardware error I had to swap bootable drives with my laptop and boot from that.

However, now I am booting from my main desktop drive, its home partition has apparently been unformatted if such a thing is possible.  The computer will not boot and the partition is visible as a RAW file system using ext2fs in windows.

Does anyone have any advice what the hell I can do to solve this - I haven't issued any formatting instructions and I would like my files back as well.  I realise a live CD will probably be involved but apart from that I am stumped.

Thanks,

---

### Post by ajgreeny on 2009-11-11
Windows is hopeless at seeing or doing anything to an ext filesystem, so you are right, boot up the live ubuntu CD and then run gparted (System -Administration -Partition Manager) to see what is actually on the disk and/or run ```
sudo fdisk -l
``` in terminal and report back here the output.  You can also mount the disk and use nautilus to see your files are still intact very easily.

---

### Post by lerrup on 2009-11-12
thanks.


The output is as follows:


Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c8bcfba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         764     6136798+  12  Compaq diagnostics
/dev/sda2   *         765       10079    74822737+   7  HPFS/NTFS
/dev/sda3           10080       17386    58693477+   c  W95 FAT32 (LBA)
/dev/sda4           17387       20023    21181702+   5  Extended
/dev/sda5           17387       18840    11679192   83  Linux
/dev/sda6           18841       19898     8498353+  83  Linux
/dev/sda7           19899       20023     1004031   82  Linux swap / Solaris


The partition I am concerned about is sda5.  GParted reports it as unknown, shows it black with a big orange triangle.  I guess this isn't a good sign...
--------------------------------------------------

After typing this I remembered fsck.  I did this and it threw up a number of errors re free space numbers, inodes, etc.  Thankfully, it was also able to repair them.

Thanks for your help, I still don't know why this happened, but at least its going again.

---

