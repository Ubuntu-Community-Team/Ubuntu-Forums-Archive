---
title: "Accidently cancelled partition"
date: 2012-03-10
forum: General Help
---

### Post by XelK on 2012-03-10
Hi All,

I accidently cancelled my home partition (ext4) from windows, and now I can mount it from Ubuntu Live. 
```

sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x96addde6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488    7  HPFS/NTFS/exFAT
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27469824   242946040   107738108+   7  HPFS/NTFS/exFAT
/dev/sda4       242948095   976773112   366912509    f  W95 Ext'd (LBA)
/dev/sda5       242948096   341348351    49200128   83  Linux
/dev/sda6       454402048   499376127    22487040   83  Linux
/dev/sda7       499378176   507772911     4197368   82  Linux swap / Solaris
/dev/sda8       507774976   976773112   234499068+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 64 MB, 64225280 bytes
2 heads, 62 sectors/track, 1011 cylinders, total 125440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bb723

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62      125363       62651   83  Linux


```
Can somebody help me???

Thanks!

---

### Post by dandnsmith on 2012-03-10
I'm not sure whether you really mean "now I can mount it from Ubuntu Live" or whether that should be 'cannot' there.

I can see there is a space in the middle of the HDD:
start around 341348352
end around 454402046
where a missing partition might be.

There are rescue tools, and I believe SystemRescueCD has some which can check for filesystems which used to be there to allow restoration.

First 'tho, is your problem a deleted partition?
if so, how did you cancel it?
and have you tried any steps so far to recover it (which may have an effect on what gets recommended).

---

### Post by oldfred on 2012-03-10
Testdisk may be able to recover partition. i think it is in dandnsmith's recommendation of SystemRescueCD.

But it also is in the repositories, so you can download into your Ubuntu liveCD.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

