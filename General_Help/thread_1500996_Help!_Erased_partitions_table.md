---
title: "Help! Erased partitions table"
date: 2010-06-03
forum: General Help
---

### Post by bizkyt on 2010-06-03
Hi, 

I was [COLOR=#000000]resizing[/COLOR] partitions wit GParted and by mistake I went to Dispositive -> Create Partitions table, and click Apply by mistake. Now all my partitions [COLOR=#000000]vanished. I already try testdisk, and gpart and didn't work.

Anyone knows how to solve this? Please help, all my files and fotos with more than 15 years [/COLOR][COLOR=#000000]vanished :|
[/COLOR]

---

### Post by bodhi.zazen on 2010-06-03
If you recall the partition scheme you can probably rebuild it with fdisk.

If not, I would assume your data is still there, try testdisk (data recovery) or photorec.

---

### Post by bizkyt on 2010-06-03
Testdisk and gpart didin't work.

"If you recall the partition scheme you can probably rebuild it with  fdisk."

How to do it?

---

### Post by bodhi.zazen on 2010-06-03
> **bizkyt said:**
> Testdisk and gpart didin't work.

"If you recall the partition scheme you can probably rebuild it with  fdisk."

How to do it?

Do you know your partition table ?

If so, sudo fdisk /dev/sda

[http://www.freeos.com/articles/3935/](http://www.freeos.com/articles/3935/)

I understand testdisk did not help, did you try to recover data with testdisk ?

1. [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search)

2. [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2)

If that fails, try photorec

3. [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by bizkyt on 2010-06-03
In testdisk when I click quick search appears this:

> 
*TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
L HPFS - NTFS              0   2  1 23869 254 63  383471424
L Linux                24762   2  1 31630 254 63  110350359
L Linux Swap           31631   1  1 31929 254 63    4803372
L HPFS - NTFS          31930   1  1 60800 254 63  463812552



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 196 GB / 182 GiB


Clicking in P in the last partition it appears that the filesystem is damaged. What can I do now?

---

### Post by bodhi.zazen on 2010-06-03
It appears your partitions were found, write them to disk

I think you hit enter, then on the next screen select write.

Once you have written your partitions you can try to reboot and fix the partitions from windows.

---

### Post by bizkyt on 2010-06-03
I already deleted windows, I only can access from live cd ..

---

### Post by bodhi.zazen on 2010-06-03
> **bizkyt said:**
> I already deleted windows, I only can access from live cd ..

OK, well, in the future, if you are going to get rid of Windows , you should also get rid of ntfs partitions as it is often difficult or impossible to fix them from Linux.

First things first, were you able to recover your partition table ?

If so, what happens when your try to access your data ?

---

### Post by bizkyt on 2010-06-03
Yes I recovered the partition table and rebooted the system, but the only drive i wanted to appear does not even show (data drive).
I only get an intentionally blank 196 Gb partition (previously windows + Ubuntu, deleted and merged), and 56Gb ubuntu of the supposly deleted. and no data partition showing anywhere.

In Gparted I get a strange error. it shows "sem alocaçao" (without allocation), and when I click in its information I get this message "Nao pode ter uma partiçao fora do disco!" (you can not have a partition out of the disk!).

EDIT: Think I'm getting the previou partition schema, before i deleted+merged+resized, problem is that I don't recall the correct sizes of the partitions.

---

### Post by bizkyt on 2010-06-06
Thank you for the help bodhi.zazen. I finally did it with the testdisk, used the deep serch and recoverd all my files. :)

---

### Post by bodhi.zazen on 2010-06-06
Great. I understand, testdisk is a bit clunky at first, but in general it works well.

---

