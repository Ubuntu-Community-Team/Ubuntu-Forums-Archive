---
title: "Gparted crashed, can no longer boot or see home folder"
date: 2012-07-18
forum: General Help
---

### Post by TheSkunkMan on 2012-07-18
Ok, I was trying to move and resize my partitions to leave a little more space ifor my windows partition and gparted decided to crash. I can no longer boot into either windows or linux. However, from a live cd I can see my windows partition which looks fine, but my ext4 partion is missing my home folder and some other stuff I assume. Also gparted also says I'm only using 14.47 GiB of my linux partition. Is there any way to restore or access my lost data? Luckily I have a backup with almost everything I need, but I have a few files I need to grab. Any help would be great

---

### Post by stepking2 on 2012-07-18
Have you tried taking out the harddrive and plugging it in a desktop computer?

---

### Post by rukiaEnix on 2012-07-18
Try using [testdisk ]("http://www.cgsecurity.org/wiki/TestDisk")with your live CD.

---

### Post by pqwoerituytrueiwoq on 2012-07-18
does gparted sow a unknown partition? it may give you a option to check and repair it in the right click menu
if that is not the case [text disk](apt:testdisk) is the way to go it is in repos

---

### Post by oldfred on 2012-07-18
Any sort of crash in the middle of a partition resize where it is moving data, causes major issues as there is no way to tell where the data is now.

You may be able to recover one or the other partition depending on where it was at. Try testdisk to see what it says.

Part of testdisk is photorec. It just scans drive for anything that looks like a file. It cannot recover filenames but looks by type and recovers extension. It is a long slow process. I did it to recover some text files. I had saved text file almost daily since backup and it found every old copy, but I was not able to tell which was the last saved. Lots of grepping & comparing to last backup, so I recovered most of my data. 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by TheSkunkMan on 2012-07-18
well testdisk tells me the "partion can't be recovered". I guess I'll see what photorec can do before giving up.

---

### Post by TheSkunkMan on 2012-07-19
Ok, photorec recovered everything I needed, but somewhere in the process I somehow change the partition table (i think) and now I cannot see my windows partition that was previously untouched. Gparted tells me 
I cannot have a partition outside the disk.
First Sector: 0
Last Sector: 488395054
Total Sectors: 488395055

Here is the output of fdisk
```
Disk /dev/sda: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9687dc04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    92366840    46079996+   7  HPFS/NTFS/exFAT
/dev/sda3        92368896   485249023   196440064   83  Linux
/dev/sda4       485249058   488408129     1579536    f  W95 Ext'd (LBA)
/dev/sda5       485251072   488394735     1571832   82  Linux swap / Solaris

```

Any help would be great because restoring my windows partition will be a hassle.

---

### Post by rukiaEnix on 2012-07-19
Maybe this post from gparted forum can help you: [http://gparted-forum.surf4.info/viewtopic.php?id=16092](http://gparted-forum.surf4.info/viewtopic.php?id=16092)

This is just a constructive critic and doesn't mean that I won't help if I see a post here asking for help: try to google all the errors you get and that way you will learn more about Ubuntu and any other things.

---

### Post by oldfred on 2012-07-19
We occassional see this error both from testdisk redoing things and some Windows partitioning tools.

The extended partition ends after the drive.

> Disk /dev/sda: 250.1 GB, 250058268160 bytes
255 heads, 63 sectors/track, 30401 cylinders, total [COLOR=Red]488395055[/COLOR] sectors


/dev/sda4       485249058   [COLOR=Red]488408129  [/COLOR]   1579536    f  W95 Ext'd (LBA)



sda4 is too large.

First backup partition table
sudo sfdisk -d /dev/sda > parts_sda.txt

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

