---
title: "GParted corrupted my ext4 / partition"
date: 2010-08-26
forum: General Help
---

### Post by dt2g on 2010-08-26
My HDD has 3 NTFS Windows Partitions (two of those are for recovery) and an extended partition containing a 250GB ext4 partition where my Lucid install lives and a 4GB linux swap partition. The other day, I shrank my 250GB Windows 7 partition by 40GB and expanded the extended partition by 40GB. When I tried to expand my ext4 partition so it would use the extra 40GB, Gparted encountered an error about halfway through reading all my data. GParted then said the partition was an "unknown" file system, and that it was either corrupt or unformatted.
 
The ext4 partition is no longer mountable or bootable, the superblock and backup superblock is undetected by fsck. I can access data off the corrupt partition through [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"), which still detects the disk as "EXT4 Large file Sparse superblock", but only in small amounts at a time.
 
I'm honestly not sure what to do at this point, besides format and start all over again. While this isn't completely out of the question, I would really rather not as I would lose around 60GB of un backed-up TV shows, movies, virtual machines, etc. as well as some program data. If someone could give me some help with fixing this, or could at least point me in the right direction, I would really appreciate it. Thanks a ton,
 
Dave

---

### Post by v1ad on 2010-08-26
i can't help you. but for the future, learn to backup :[

---

### Post by Sef on 2010-08-26
> The other day, I shrank my 250GB Windows 7 partition by 40GB

How did you shrink the partition?

---

### Post by dt2g on 2010-08-26
> **Sef said:**
> How did you shrink the partition?
 I used Windows 7's built in partition management tool, diskmgmt.msc

---

### Post by dt2g on 2010-08-27
Bump

---

### Post by Rubi1200 on 2010-08-27
Try using testdisk or the LiveCD to get the files off the partition.

Also, while using the LiveCD, please post the output of the bootscript linked to at the bottom of my post.

Thanks and good luck :)

---

### Post by dt2g on 2010-08-27
> **Rubi1200 said:**
> Try using testdisk or the LiveCD to get the files off the partition.

Also, while using the LiveCD, please post the output of the bootscript linked to at the bottom of my post.

Thanks and good luck :)
Thanks for the reply!  The output of the bootscript is as follows: ```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    18,089,983    18,087,936  27 Hidden HPFS/NTFS
/dev/sda2    *     18,089,984    18,296,831       206,848   7 HPFS/NTFS
/dev/sda3          18,296,832   368,597,039   350,300,208   7 HPFS/NTFS
/dev/sda4         368,597,040   976,773,119   608,176,080   5 Extended
/dev/sda5         968,773,632   976,773,119     7,999,488  82 Linux swap / Solaris
/dev/sda6         452,486,853   968,767,694   516,280,842  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E23CAEC73CAE95D7                       ntfs       Recovery                      
/dev/sda2        C6C2DAD5C2DAC937                       ntfs       System Reserved               
/dev/sda3        BCBADC92BADC4B12                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        160fd35e-7506-4bcc-8014-9f13636b7bc5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

```If you need some background info, /dev/sda6 is/was my ext4 / partition, as well as the partition where GRUB2 was installed to.

---

### Post by Rubi1200 on 2010-08-27
The bootscript confirms what you kind of already knew; the Ubuntu partition is lost.

As I said before, try and recover at least some of the data.

Afterwards, you have little choice but to reinstall.

I would probably use GParted from the LiveCD to format the partition first.

Let us know if you have any questions.

---

### Post by dt2g on 2010-08-27
> **Rubi1200 said:**
> The bootscript confirms what you kind of already knew; the Ubuntu partition is lost.

As I said before, try and recover at least some of the data.

Afterwards, you have little choice but to reinstall.

I would probably use GParted from the LiveCD to format the partition first.

Let us know if you have any questions.
Yeah, this doesn't come as much of a surprise.  Thanks for your help though, at least now that I know it's game over I can start rebuilding my system.

Dave

---

