---
title: "testdisk and data loss"
date: 2009-12-19
forum: General Help
---

### Post by catonic on 2009-12-19
Hi, I have found I can no longer access my backup files on an external hard drive and have tried a number of different things including dd_rescue and photorec but have run into various problems.
Anyway, here is what testdisk says:

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdf - 200 GB / 186 GiB - CHS 24321 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P FAT32 LBA                0  32 33  2549 228 47   40962048 [SDD1-FAT32-]
 2 E extended LBA          2550   0  1 15851 254 63  213696630
 3 P HPFS - NTFS          15852   0  1 24320 254 63  136054485 [Programs]
No partition is bootable
 5 L Linux Swap           14023   1  1 14284 254 63    4208967
   X extended             14285   0  1 15365 254 63   17366265
No EXT2, JFS, Reiser, cramfs or XFS marker
 6 L Linux                14285   1  1 15365 254 63   17366202
 6 L Linux                14285   1  1 15365 254 63   17366202
   X extended             15366   0  1 15851 254 63    7807590
No EXT2, JFS, Reiser, cramfs or XFS marker
 7 L Linux                15366   1  1 15851 254 63    7807527
 7 L Linux                15366   1  1 15851 254 63    7807527
   X extended              2550   0  2 14022 254 63  184313744
No EXT2, JFS, Reiser, cramfs or XFS marker
 8 L Linux                 2550   2  1 14022 254 63  184313619
 8 L Linux                 2550   2  1 14022 254 63  184313619

I want to recover the linux partitions which should be reiserfs. I have tried to use reiserfsk to restore/rebuild but it did not work.
Any advice welcome. Thanks.

---

### Post by bodhi.zazen on 2009-12-19
If those tools are failing you, and you "need" the data, I suggest you seek out professional advice and stop messing with the drive yourself.

---

### Post by catonic on 2009-12-20
I have used dd_rhelp to create a disk.dump file which is the same size as the partition and below is the disk.dump.log:

=== COMPUTED VERSION OF LOG :
chunk:
logcontent:
eof:nothing
=== parsing at 0k, for 0k, max continuous err: 2.5k >>> ===
dd_rescue: (info): ipos:  92156800.0k, opos:  92156800.0k, xferd:  92156800.0k
                   errs:      0, errxfer:         0.0k, succxfer:  92156800.0k
             +curr.rate:     7882kB/s, avg.rate:     8231kB/s, avg.load:  4.7%
dd_rescue: (info): /dev/sdf8 (92156809.5k): EOF
Summary for /dev/sdf8 -> /media/sdb5-195/disk.dump:
dd_rescue: (info): ipos:  92156809.5k, opos:  92156809.5k, xferd:  92156809.5k
                   errs:      0, errxfer:         0.0k, succxfer:  92156809.5k
             +curr.rate:     4396kB/s, avg.rate:     8231kB/s, avg.load:  4.7%
=== COMPUTED VERSION OF LOG :
chunk:0-92156809.5
logcontent:ipos=92156809.5:xferd=92156809.5:NR:errxfer=0.0:succxfer=92156809.5
eof:92156809.5

Could someone please tell me how to access the disk.dump file which I assume contains my files. Thanks.

---

### Post by bodhi.zazen on 2009-12-20
See this thread :

[http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

Post 2

---

