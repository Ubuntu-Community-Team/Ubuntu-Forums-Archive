---
title: "dd gets slower [8*MB/s -&gt; 0.7MB/s]"
date: 2010-12-15
forum: General Help
---

### Post by pir on 2010-12-15
root@karlo-laptop:/home/karlo# dd if='/home/karlo/Images/image-2GiB.img' of=/dev/sdb bs=32k

6547+0 records in
6547+0 records out
214532096 bytes (215 MB) copied, 27.4087 s, 7.8 MB/s
8772+0 records in
8772+0 records out
287440896 bytes (287 MB) copied, 111.087 s, 2.6 MB/s
9607+0 records in
9607+0 records out
314802176 bytes (315 MB) copied, 145.438 s, 2.2 MB/s
10469+0 records in
10469+0 records out
343048192 bytes (343 MB) copied, 179.591 s, 1.9 MB/s
^T10898+0 records in
10898+0 records out
357105664 bytes (357 MB) copied, 196.665 s, 1.8 MB/s
11745+0 records in
11745+0 records out
384860160 bytes (385 MB) copied, 230.842 s, 1.7 MB/s
14212+0 records in
14212+0 records out
465698816 bytes (466 MB) copied, 334.353 s, 1.4 MB/s
15514+0 records in
15514+0 records out
508362752 bytes (508 MB) copied, 386.381 s, 1.3 MB/s
21488+0 records in
21488+0 records out
704118784 bytes (704 MB) copied, 625.928 s, 1.1 MB/s
27047+0 records in
27047+0 records out
886276096 bytes (886 MB) copied, 848.281 s, 1.0 MB/s
35960+0 records in
35960+0 records out
1178337280 bytes (1.2 GB) copied, 1207.6 s, 976 kB/s
49342+0 records in
49342+0 records out
1616838656 bytes (1.6 GB) copied, 1731.4 s, 934 kB/s
55628+0 records in
55628+0 records out
1822818304 bytes (1.8 GB) copied, 2001.87 s, 911 kB/s
60352+0 records in
60352+0 records out
1977614336 bytes (2.0 GB) copied, 2574.92 s, 768 kB/s
60352+0 records in
60352+0 records out
1977614336 bytes (2.0 GB) copied, 2574.92 s, 768 kB/s

How is this possible? I am copying to a USB microSD card. 

root@karlo-laptop:/home/karlo# uname -a
Linux karlo-laptop 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

---

### Post by Spyderkid on 2010-12-15
micro SD is very slow its flash memory so it might get slower the more you copy

---

### Post by hkazemi on 2011-02-17
I sometimes experience this problem while dd'ing* partition images back to partitions.  Running Ubuntu 10.04.2 LTS (Lucid).

Sometimes if I run the same command a second time it goes through fast (although speed fluctuates around a lot), other times performance degrades from 16 MB/s to 0.25 MB/s and stays slow even after leaving the process run for 10 hours.

One time I experienced it while imaging from an image file on an external NTFS formatted USB hard drive to a partition on an internal SATA drive.  I thought the NTFS-3G driver might be at fault so I copied the image file to an EXT4 partition on a different internal SATA drive.  The problem still occurred.  As such I don't believe the NTFS-3G is the root cause because the problem still occurred even with NTFS out of the picture.

No solution found so far.  Will test ddrescue next.

---
* I encountered this while using dd through Clonezilla.  I manually installed Clonezilla on Ubuntu using the guide at [http://ubuntuforums.org/showthread.php?t=1216081](http://ubuntuforums.org/showthread.php?t=1216081) .  I also added pbzip2 (Jeff Gilchrist's version).  Clonezilla uses dd via scripts to save and restore partition types that partimag doesn't support (e.g. EXT4).  The slowness I experienced is coming when dd is asked to write the image back to the drive.


The SATA controller is 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller

Drive being read from is a Seagate ST3500320AS 3.5" 500gb 7200 rpm drive.
Drive being written to is a Hitachi HTS725032A9A364 2.5" 320gb 7200 rpm 7K500 drive.

---

