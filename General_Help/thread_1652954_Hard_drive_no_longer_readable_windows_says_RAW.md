---
title: "Hard drive no longer readable windows says RAW?"
date: 2010-12-25
forum: General Help
---

### Post by drswingingblades on 2010-12-25
Ive looked through a few threads but i cant find any direct help for my issue

i have over 300 GB of movies saved on my external FAT32 (out of date, but its necessary for PS3)

I ALWAYS eject it safely for i dont want to corrupt the drive. Well for some reason now Ubuntu nor windows can read it

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    b  W95 FAT32

```

the drive is tthere but it wont mount

---

### Post by indike on 2010-12-26
Try using mount command in Terminal as root:

sudo mount /dev/sdc1 /media/(disk)

*(disk) can be any folder inside /media

---

### Post by drswingingblades on 2010-12-26
```
matthew@matthew-P-7805u:~$ sudo mount -t vfat /dev/sdc1 /media/external
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by drswingingblades on 2010-12-26
please, need some help recovering my files

---

### Post by veggen on 2010-12-26
I'd honestly try repairing from Windows, it's much easier if you're not all that proficient. There are many partition restoring freeware programs that should be able to help you. I have a good experience with Partition Find & Mount. If you can't restore the partition, try any of the file recovering utilities, they all work with FAT32.

---

### Post by WthIteh on 2010-12-26
Use
```

sudo fsck.vfat -r /dev/sdc1

```

---

### Post by oldfred on 2010-12-26
If the partition is RAW, it means it has lost its boot sector. Windows parititons have to have both be formated and have a matching boot sector that has the correct start & end points for the partition and some code for booting windows if it is installed.

You can use a windows repair CD and run fixboot (XP). or from Vista/7 use bootsect to update bootsector.

From Ubuntu you can download testdisk and have it rebuild the bootsector. I know it works for NTFS and expect it to also work for FAT.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by drswingingblades on 2010-12-26
So i ran TestDisk on this drive and the program doesn't find any sort of partition at all? So I guess I'm to assume that I've lost all my movies?

after running the disk check i get this

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdc - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors




Structure: Ok.


Keys A: add partition, L: load backup, Enter: to continue
```

---

### Post by oldfred on 2010-12-26
Testdisk normally finds things. Did you try deeper search?

Next is photorec which is part of testdisk. It just scans a drive for things that look like files. It does not recover file names, but photos and music have internal data to recreate names.

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

---

### Post by drswingingblades on 2010-12-26
I didnt see the Deeper search till after i posted, im doing the deeper search now 20%, huge drive though so it takes a while

ill reply with the results

thanks for the help oldfred

---

### Post by drswingingblades on 2010-12-26
After deeper search I found the partition and it said it was deleted, I am in process of copying all the files onto another hdd, itll take a while but im pretty sure my problem is solved. TestDisk is the best recovery program ive ever used so powerful.

thanks oldfred

---

