---
title: "Unsusal RAID 1 Array degraded"
date: 2009-09-18
forum: General Help
---

### Post by BarryDocks on 2009-09-18
Hi there hope someone can shed some light on this one.  I have a small file/print server running ubuntu 8.04 server 64bit edition.  I have 2x20GB drives set up as a RAID 1 for the md0 for the OS and md1 for swap. I also have 4x250GB drives as RAID10 for network storage.  Recently I have has the following message from the mdadm daemon:> From: mdadm monitoring <root@fileserver>
To: root@fileserver
Subject: DegradedArray event on /dev/md0:fileserver
Message-Id: <E1MoMIb-0001ci-Ct@fileserver>
Date: Thu, 17 Sep 2009 20:05:45 +0100

This is an automatically generated mail message from mdadm
running on fileserver

A DegradedArray event had been detected on md device /dev/md0.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid10 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      488391808 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      
md1 : active raid1 sde2[0] sdf2[1]
      995904 blocks [2/2] [UU]
      
md0 : active raid1 sde1[0]
      18554944 blocks [2/1] [U_]

Sure enough, running **cat /proc/mdstat** gives:
> md2 : active raid10 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      488391808 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      
md1 : active raid1 sde2[0] sdf2[1]
      995904 blocks [2/2] [UU]
      
md0 : active raid1 sde1[0]
      18554944 blocks [2/1] [U_]
      
unused devices: <none>

To me this means that both drives are functioning for the swap partition but only one for the OS partition, is this possible? I assumed that when a drive failed it would degrade all the partitions on it? 

was going to follow this howto in order to rebuild the array with the same drives:
[http://www.technibble.com/forums/showthread.php?p=70618]("http://www.technibble.com/forums/showthread.php?p=70618")

First I would like to copy the contents of the Array to a separated external drive in case it all goes wrong, ie ghost it - any suggestions on the best way to do this?

Thanks

---

