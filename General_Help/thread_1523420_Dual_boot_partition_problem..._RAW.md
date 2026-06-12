---
title: "Dual boot partition problem... RAW?"
date: 2010-07-03
forum: General Help
---

### Post by swallow on 2010-07-03
Hello!  I should start off by saying that I am very new to Ubuntu, so I'm really learning as I go here.

I'm running a dual boot of Ubuntu 9.10 and Windows 7.  For months now everything has been just wonderful.  Recently, however, I tried to add another partition (in windows) and saw that my Ubuntu partition is recognized as RAW.  I formatted it as NTFS orginally.  In Ubuntu, it is recognized correctly (ext4).

I don't know what's going on.  I'd like to be able to install drivers to recognize this partition in Windows.  Will I have to reformat?

I'm not sure if it's at all connected, but probably worth mentioning: while booting into Ubuntu, I received an error about "usplash mode failed."  It also said something about "mount of filesystem failed."  (I really, really wished I had written down the error message.)  Everything seems to work now.

I would really appreciate any help people could offer!

---

### Post by spiky001 on 2010-07-03
Take a look here
[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

---

### Post by swallow on 2010-07-03
Thanks :)  I've already tried installing those, with no luck.  My partition isn't recognized at all.

---

### Post by oldfred on 2010-07-03
Can you see the partition from disk utility in system, administration.

What does this show.

```
sudo fdisk -l
```

---

### Post by swallow on 2010-07-03
this is what I got: 

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60366036

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27273   219070341    7  HPFS/NTFS
/dev/sda2           27274       30401    25125660    5  Extended
/dev/sda5           27274       30266    24041241    7  HPFS/NTFS
/dev/sda6           30267       30401     1084356   82  Linux swap / Solaris

Disk /dev/sdb: 2003 MB, 2003795968 bytes
32 heads, 63 sectors/track, 1941 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x01206638

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1941     1956496+   6  FAT16


---

### Post by oldfred on 2010-07-03
sda5 is showing as 7 which is NTFS. If you are sure it is ext then you could try in disk utility changing it to ext4, but it may not let you.

If all else fails I would try testdisk. If often shows partition history and lets you choose one from the history.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by swallow on 2010-07-03
Thank you!!! Testdisk did the job.  What a handy little program.

Everything is working now.  I'm using Ext2explore and happily moving files between operating systems.  I guess this one can be marked as solved :D

---

