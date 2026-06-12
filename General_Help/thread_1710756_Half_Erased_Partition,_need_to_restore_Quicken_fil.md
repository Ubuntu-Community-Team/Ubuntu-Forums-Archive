---
title: "Half Erased Partition, need to restore Quicken file"
date: 2011-03-20
forum: General Help
---

### Post by mlapaglia on 2011-03-20
I have a HP DV9000 laptop. The second hard drive bay doesn't support SATA II devices. I was cloning the original hard drive to the newer SATA II hard drive I purchased two swap them because bay 1 does support SATA II devices. I decided to use
```
dd if=/dev/sda of=/dev/sdb
``` to get the job done. I double/triple checked my command with fdisk -l, but my dyslexia got the better of me. I should have ran ```
dd if=/dev/sdb of=/dev/sda
```....

I stopped the command about 1/2 hour in, it is a 160GB hdd. I tried using foremost to recover all of the files that hadn't been written over yet, but it can't recover Quicken filetypes. The ONLY thing I need off of this drive is the Quicken database.

TL;DR I need to recover a quicken database file off my corrupted partition. What program can I use?

---

### Post by blueridgedog on 2011-03-20
I would see if testdisk could restore the prior partition table, if so, it may be that the file you seek was not in an area that was overwritten.  At this point the drive is toast from a functionality standpoint, so you have little risk in trying testdisk.  You can use it from a LiveCD.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

and

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

When booted on a LiveCD with network access, you can install testdisk with:


sudo apt-get install testdisk

---

