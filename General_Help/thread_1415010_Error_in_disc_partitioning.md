---
title: "Error in disc partitioning"
date: 2010-02-24
forum: General Help
---

### Post by jw1949 on 2010-02-24
I am new to Linux and think I may have messed up when I partitioned this disc at installation time.  I have a 500Gb disc - File system (sda1) is 100Gb (analyser says 33% used); there's a 526Mb partition (sda4) where I have another linux install ??? and a 63Gb partition (sda3) for the contents of the c: drive from my (defunct) WinXP system.

 * Screenshot is attached*

I guess I have setup 160GB+ and the remainder is not available??

How can I get at this and/or re-partition to utilise it ?

Thx in advance.

---

### Post by dabl on 2010-02-24
Looks kinda messed up.  I have always found it helpful to separate the process of partitioning a hard from the process of installing the OS.  Download the ISO file and burn a Parted Magic Live CD from here:  [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

This is a very handy Live CD that has numerous useful utilities including a GUI for smartmon tools that makes it easy to test hard drives.

So, boot your Parted Magic Live CD and partition your hard drive as you actually want it.  Here's some guidance:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

When you have the hard drive partitioned the way you want it, THEN take your *buntu Live CD or Alternate Install CD (my favorite) and boot it and install the OS on the partitions that you already have waiting for you.  :)

---

### Post by SecretCode on 2010-02-24
Your screenshots tell us what's mounted, but not all the details of what's on the drive.

Can you go to a terminal window and post the output of:
```
sudo fdisk -l
```

---

### Post by jw1949 on 2010-02-25
Thx for the responses - I have fiddled around with GParted as you suggested and managed to create an extended partition and use the full disc.   The reading you suggested was very worthwhile - thanks for pointing me in exacttly the right direction!

The output from sudo fdisk -l is below (after the changes!!):

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003fbb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         128       12876   102406342+  83  Linux
/dev/sda2           20526       60801   323516970    5  Extended
/dev/sda3           12877       20525    61440592+   7  HPFS/NTFS
/dev/sda4               1         127     1020096   83  Linux
/dev/sda5           60145       60275     1052226   82  Linux swap / Solaris
/dev/sda6           20526       33579   104856192   83  Linux
/dev/sda7           33580       46633   104856223+  83  Linux
/dev/sda8           46634       60144   108527076   83  Linux
/dev/sda9           60276       60801     4225063+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b2461bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12187    97892046    7  HPFS/NTFS

---

### Post by SecretCode on 2010-02-25
So, are you all sorted now? If so, you can mark the thread solved, via the 'Thread tools' menu.

---

