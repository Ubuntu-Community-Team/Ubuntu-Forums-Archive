---
title: "AA1Backup problem"
date: 2012-02-07
forum: General Help
---

### Post by WinfriedG on 2012-02-07
Since 2008 I aim using the AA1backup programme to backup or recover my SSD to/from a USB Hard drive.
Now I want to use my Samsung USB minidisk (32GB) which I have completely reformated in order to get rid of all kind of junk.
Then I wanted to install AA1backup on this drive. I created a 8GB FAT 32 primary partition on this minidisk as first partition.
Then I started the installation of the programme from a terminal (OS is Lubuntu11-10) with the command
```
chmod 755 aa1blinux && sudo ./aa1blinux
```and got a message saying

> vol_id not found. This is required for either install mode. Install the "udev" package or your distro's equivalentWell udev is installed. And gparted identifies the partition as sdb1.

By the way: some two years ago I succeeded to install AA1backup on that drive in the first partition and did the backup eg under Fedora or Mandriva on that drive. For other use of the Harddrive I deleted the partition three month ago. On a USB stick the backup and recovery with this programme works very well.  

Any idea?

_________
**Winfried**G
AAO-Z5 since end of  2008; 512MB RAM; 8GB SSD; 16GB SD extension  started with Linpus Lite; changed 2009 to  Fedora 11; 2010  to Mandriva; March 2011 to F14 LXDE;  4 Feb 12 Lubuntu  11.10 ;  wireless USB mouse; firefox & thunderbird 10; libre office;  bluetooth; Wacon tablet

---

### Post by cavalier911 on 2012-02-07
aa1backup is not being updated.
Linux software needs to be updated as linux changes or it stops working:
[http://www.rebelzero.com/ubuntu/9-10-karmic-koala/karmic-drops-vol_id-superceded-by-blkid/190](http://www.rebelzero.com/ubuntu/9-10-karmic-koala/karmic-drops-vol_id-superceded-by-blkid/190)

None of the current distro's I use support the vol_id command 
If the source code was available for aa1backup it could be configured to use blkid and recompiled to make it work.
Or there may be some type of wrapper script that could be written so when vol_id is called it executes blkid instead.

The vol_id issue may only involve the installation of aa1backup.
You should be able to install it with a pre Karmic version of ubuntu running from a live cd.
There is also a version that runs on WinXP:
[http://macles.blogspot.com/2008/12/acer-aspire-one-aa1backup.html](http://macles.blogspot.com/2008/12/acer-aspire-one-aa1backup.html)

---

### Post by WinfriedG on 2012-02-07
Oha; that is trist, since AA1backup is such a useful tool for people with a SSD. I hope that macles provides the sourcecode of his programme. Then somebody in the acer aspire user forum should maintain this programme. Unfortunately I don't have suffcient knowlegde in programming to be that person. My last programming was 30 years ago in Fortran and PL1.

---

