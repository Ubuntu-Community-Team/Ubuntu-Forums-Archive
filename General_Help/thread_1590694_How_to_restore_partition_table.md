---
title: "How to restore partition table?"
date: 2010-10-08
forum: General Help
---

### Post by adummy on 2010-10-08
I got swap space full error and the ubuntu version of "blue screen of death". I used Disk Utilities to delete a 2.1GB unused partition. When I tried to create a swap space partition (with Disk Utilities) it failed. In the mean time ubuntu did some security updates. When I tried to create again Disk Uilities did not complain but only created a small ~ 500 kB partition. I deleted that and reboot and got "unknown filesystem grub rescue>". I booted from a USB key successfully. Now Disk Utilities and File Browser can see all the partitions and files on the hard drive, but GParted thinks the entire hard drive is unallocated. :confused: I vaguely remember that there are two partition table on the hard drive. It may be that one of them was deleted (when I removed the ~ 500 kB partition with Disk Utilities earlier maybe?). It seems at least the other partition table is still intact since Disk Utilities and File Browser can still see all the partitions and files. Is it possible to restore the deleted or damaged partition table and make the hard drive bootable again? Thanks!

---

### Post by iiiears on 2010-10-08
Likely it didn't write everything to disk before power-off and is trying to 'help' you by marking the disk for a file system check on the next reboot. (fsck)

If you get a copy of testdisk photorec it can sometimes find the error. It's slow the man pages are a wall of rext. Really. not fun at all until you have done it a few times.

---

### Post by adummy on 2010-10-08
> **iiiears said:**
> Likely it didn't write everything to disk before power-off and is trying to 'help' you by marking the disk for a file system check on the next reboot. (fsck)

If you get a copy of testdisk photorec it can sometimes find the error. It's slow the man pages are a wall of rext. Really. not fun at all until you have done it a few times.

Thanks for helping! :) I am running testdisk and it says
> 
test_logical:
Partition sector doesn't have the endmark 0xAA55

:confused:
What to do next? Thanks!

---

### Post by iiiears on 2010-10-08
I am not familiar with that error but a quick search turned up mention that it, might, maybe, couldbe. ought to be if the google gods are smiling, be the "Verification Boot Record. a second 'backup' descriptor if the nearly always reliable and Master Boot Record. 

What does it mean and what to do? Google or or gamble for a shot in the dark and allow testdisk to rewrite the mbr boot record as it was. Steady now.. It is all to easy to F... up - err. "make a mistake" and cast binary bits into the non-retrievable void of nothingness. 

Google a bit more and i will too for the next 20 mins and see if we can turn up something. It's almost certain i will know more than i do now.(shrugs)

---

### Post by drs305 on 2010-10-08
When I use TestDisk I always refer to one or both of these links:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status")

[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/~herman546/p21.html")

---

### Post by adummy on 2010-10-08
> **iiiears said:**
> I am not familiar with that error but a quick search turned up mention that it, might, maybe, couldbe. ought to be if the google gods are smiling, be the "Verification Boot Record. a second 'backup' descriptor if the nearly always reliable and Master Boot Record. 

Yes this sounds exactly right! :) I suspect the File Browser and the Disk Utility do not look at that "backup" so they have no problem seeing all the partitions and files. On the other hand GParted may need that "backup" to be correct to work: right now it thinks the entire physical hard drive is unallocated - no partition at all!

> 
What does it mean and what to do? Google or or gamble for a shot in the dark and allow testdisk to rewrite the mbr boot record as it was. Steady now.. It is all to easy to F... up - err. "make a mistake" and cast binary bits into the non-retrievable void of nothingness. 

Google a bit more and i will too for the next 20 mins and see if we can turn up something. It's almost certain i will know more than i do now.(shrugs)

Yes I am also googling but my google skill is really poor. I will keep trying to see if anything come up. Is there an option in testdisk to rewrite the MBR as is? I didn't see that after hit enter for "Quick Search". It only gave me options of modifying a selected partition which I don't intend to do. 

Right now I am in BIOS doing hard disk self test. So far so good.

 Thanks again! :)

---

### Post by iiiears on 2010-10-08
Here?
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)

If your data is one of a kind database,photos or expensive Itunes, Downloaded games etc. Grab a USB enclosure and hard disk. Gddrescue and virtualbox/vmware will image it mount it and reconstruct the data after a bit of research.

A little waiting and a guru will see this thread. Right?

---

### Post by adummy on 2010-10-08
> **drs305 said:**
> When I use TestDisk I always refer to one or both of these links:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status)

[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")

> **iiiears said:**
> Here?
[http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)


Thanks very much for the links! I will be studying...

This seems interesting:
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
near the end of the web page:
> MBR Code = Write TestDisk MBR code to the first sector (similar to **fdisk**, includes **aa55 **sig too)
--> Write a new copy of MBR code to first sector? (Y/N)
But the earlier error was saying partition, not boot record. On the other hand the main problem is the hard disk can't boot. At any rate it should re-write whatever used to be on the hard disk, not some new default MBR (which I though fdisk does), right? (I have Ubuntu, Vista, and XP on the hard disk)

---

### Post by iiiears on 2010-10-08
One of the boot records is likely right but which one?
I don't recall any way to undo a 50/50 choice if it is the wrong one. Likely someone else can but i would be lost.
At this point i would buy a new drive and image the old one to it. Learning what happened has got to be more interesting than T.V.

---

### Post by adummy on 2010-10-08
and this is staring at my face and I missed it at the first glance:

[http://www.cgsecurity.org/wiki/Data_Recovery_Examples](http://www.cgsecurity.org/wiki/Data_Recovery_Examples)

> 
**  The type of the file system is RAW - Recovery of a damaged FAT boot sector **

 Analyse Disk 80 - CHS 3737 255 63 - 29313 MB (Enh BIOS mode) 1 * FAT32                    0   1  1   382 254 63    6152832 [LOKAL DISK] 2 E extended LBA           383   0  1  3736 254 63   53882010 [SIZE=4]**Partition sector doesn't have the endmark 0xAA55 **[/SIZE]5 L FAT32                  383   1  1  3736 254 63   53881947 5 L FAT32                  383   1  1  3736 254 63   53881947 

---

### Post by iiiears on 2010-10-08
Maybe another option.
[http://technet.microsoft.com/en-us/library/cc736327(WS.10).aspx](http://technet.microsoft.com/en-us/library/cc736327(WS.10).aspx)

---

### Post by iiiears on 2010-10-08
When all else fails.
[http://www.runtime.org/](http://www.runtime.org/)

---

### Post by srs5694 on 2010-10-08
First, some comments on previous posts:


[LIST]
[*]It's important to understand the different layers of data structures. A partition table defines the start and end points of partitions, along with a few pieces of metadata (such as a partition type code). Partition tables are fairly simple. The partitions defined by partition tables usually contain filesystems, which are much more complex data structures. (Partitions can also hold swap space or other types of data.) A single partition table typically defines several partitions. It's possible to damage the whole partition table, a single partition table entry, or the filesystem data structures inside one or more partitions. Each type of damage has its own symptoms and possible methods of recovery.
[*]The Master Boot Record (MBR) partitioning system does not include any backup data structures by default, contrary to what some have suggested. If the MBR gets wiped or damaged, that's it; there's no way to recover except by scanning the disk in hopes of locating "signatures" for individual filesystems and re-creating the partition table from that. The new GUID Partition Table (GPT) partitioning system, by contrast, *does* include backups of its data structures and so is more resistant to some types of damage; however, GPT is uncommon on commodity PCs. (It's standard on new Macs, and you can choose to install Ubuntu using GPT.) It's unwise, but not impossible, to put both MBR and GPT data on a single disk. (Doing so results in a [hybrid MBR,]("http://www.rodsbooks.com/gdisk/hybrid.html") which is ugly, dangerous, and unfortunately used by Apple's Boot Camp to dual-boot Windows and OS X.)
[*]0xAA55 is, in hexadecimal, a "signature" for the MBR partition table. The error message about this code being missing probably means that the MBR's partition table has been damaged. I'm not familiar with the precise error message, though; it's conceivable that it's referring to something else.
[/LIST]


Now, moving forward: I recommend that adummy boot an Ubuntu live CD or a recovery system like [Parted Magic]("http://partedmagic.com") or [System Rescue CD,]("http://www.sysresccd.org") launch a text-mode shell, and type "sudo fdisk -lu". Post the results, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to improve legibility. This will show us what the MBR partition table looks like and whether it's damaged.

If the MBR is badly damaged, using TestDisk might recover it; however, that's not guaranteed. As a general rule, I recommend holding off on using TestDisk until the nature of the problem is understood, since TestDisk can get it wrong.

The initial symptoms (missing partitions in GParted or other libparted-based tools when you know they exist) can be caused by malformed, but not completely erased, partition table, as described [here.]("http://www.rodsbooks.com/missing-parts/") The 0xAA55 error, however, suggests that the problem may be more severe than that.

---

### Post by iiiears on 2010-10-08
Absolutely, the most informative post I have read in a very long time. Thank You VERY much.

regards,

---

### Post by adummy on 2010-10-08
> **srs5694 said:**
> First, some comments on previous posts:


[LIST]
[*]It's important to understand the different layers of data structures. A partition table defines the start and end points of partitions, along with a few pieces of metadata (such as a partition type code). Partition tables are fairly simple. The partitions defined by partition tables usually contain filesystems, which are much more complex data structures. (Partitions can also hold swap space or other types of data.) A single partition table typically defines several partitions. It's possible to damage the whole partition table, a single partition table entry, or the filesystem data structures inside one or more partitions. Each type of damage has its own symptoms and possible methods of recovery.
[*]The Master Boot Record (MBR) partitioning system does not include any backup data structures by default, contrary to what some have suggested. If the MBR gets wiped or damaged, that's it; there's no way to recover except by scanning the disk in hopes of locating "signatures" for individual filesystems and re-creating the partition table from that. The new GUID Partition Table (GPT) partitioning system, by contrast, *does* include backups of its data structures and so is more resistant to some types of damage; however, GPT is uncommon on commodity PCs. (It's standard on new Macs, and you can choose to install Ubuntu using GPT.) It's unwise, but not impossible, to put both MBR and GPT data on a single disk. (Doing so results in a [hybrid MBR,]("http://www.rodsbooks.com/gdisk/hybrid.html") which is ugly, dangerous, and unfortunately used by Apple's Boot Camp to dual-boot Windows and OS X.)
[*]0xAA55 is, in hexadecimal, a "signature" for the MBR partition table. The error message about this code being missing probably means that the MBR's partition table has been damaged. I'm not familiar with the precise error message, though; it's conceivable that it's referring to something else.
[/LIST]


Now, moving forward: I recommend that adummy boot an Ubuntu live CD or a recovery system like [Parted Magic]("http://partedmagic.com") or [System Rescue CD,]("http://www.sysresccd.org") launch a text-mode shell, and type "sudo fdisk -lu". Post the results, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to improve legibility. This will show us what the MBR partition table looks like and whether it's damaged.

If the MBR is badly damaged, using TestDisk might recover it; however, that's not guaranteed. As a general rule, I recommend holding off on using TestDisk until the nature of the problem is understood, since TestDisk can get it wrong.

The initial symptoms (missing partitions in GParted or other libparted-based tools when you know they exist) can be caused by malformed, but not completely erased, partition table, as described [here.]("http://www.rodsbooks.com/missing-parts/") The 0xAA55 error, however, suggests that the problem may be more severe than that.

Thank you!

Here is the output of fdisk:
```

ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (8)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb90883c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    59538062    29769000    7  HPFS/NTFS
/dev/sda2        59552955    90269234    15358140    7  HPFS/NTFS
/dev/sda3        90269694   182418074    46074190+   f  W95 Ext'd (LBA)
/dev/sda4       182418075   195366464     6474195    7  HPFS/NTFS
/dev/sda5       131328000   182418074    25545037+   7  HPFS/NTFS
/dev/sda6        90269696   125583359    17656832   83  Linux
/dev/sda7       125585408   127217663      816128   82  Linux swap / Solaris

Partition table entries are not in disk order


```

and here are "screen shots" of testdisk:

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - ATA ST9100827AS

Hidden sectors are present.

size       195371568 sectors
user_max   195371568 sectors
dco        195371568 sectors
Device Configuration Overlay (DCO) present.


[ Continue ]  Continue even if there are hidden data


```
Hidden sectors?  :confused:  The size is the entire disk. Maybe this is why GParted thinks the entire disk is unallocated?

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12161 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3706  18 39   59538000
 2 P HPFS - NTFS           3707   0  1  5618 254 63   30716280 [XP]
 3 E extended LBA          5619   7 19 11354 254 63   92148381
 4 P HPFS - NTFS          11355   0  1 12160 254 63   12948390 [PRESARIO_RP]
 5 L HPFS - NTFS           8174 201 28 11354 254 63   51090075 [Home]
   X extended              5619   7 20  7817  51 42   35313665
 6 L Linux                 5619   7 21  7817  51 42   35313664
   X extended              7817  51 43  7918 237 63    1634304
 7 L Linux Swap            7817  84 12  7918 237 63    1632256
   X extended              7919   0  1  8173 254 63    4096575

[B]test_logical:
Partition sector doesn't have the endmark 0xAA55
[/B]

*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

```
All the partitions are there as they should be. What's the problem?


```


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12162 255 63

The harddisk (100 GB / 93 GiB) seems too small! (< 106 GB / 99 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  HPFS - NTFS          12160 254 63 12966 254 61   12948389


[ Continue ]
NTFS, 6629 MB / 6322 MiB


```
I think this is OK. Just a remnant of previous partition changes.

```


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12162 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  3706 254 63   59552892
P HPFS - NTFS           3707   0  1  5618 254 63   30716280 [XP]
L HPFS - NTFS           5619   2  1  7918 254 63   36949374 [Ubuntu]
L HPFS - NTFS           8174 201 28 11354 254 63   51090075 [Home]
P HPFS - NTFS          11355   0  1 12160 254 63   12948390 [PRESARIO_RP]


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 30 GB / 28 GiB

```
How come searching found fewer partitions than current?  :confused:  Does this mean some of the current partitions are corrupted?


```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12162 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  3706 254 63   59552892
P HPFS - NTFS           3707   0  1  5618 254 63   30716280 [XP]
D HPFS - NTFS           5619   2  1  7918 254 63   36949374 [Ubuntu]
L HPFS - NTFS           8174 201 28 11354 254 63   51090075 [Home]
P HPFS - NTFS          11355   0  1 12160 254 63   12948390 [PRESARIO_RP]


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 18 GB / 17 GiB

```
Comparing to the current partitions I marked two "bad" ones to be deleted.


```


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 100 GB / 93 GiB - CHS 12162 255 63

     Partition                  Start        End    Size in sectors

 1 P HPFS - NTFS           3707   0  1  5618 254 63   30716280 [XP]
 2 E extended LBA          8174 201  1 11354 254 63   51090102
 3 P HPFS - NTFS          11355   0  1 12160 254 63   12948390 [PRESARIO_RP]
 5 L HPFS - NTFS           8174 201 28 11354 254 63   51090075 [Home]



[  Quit  ]  [Deeper Search]  [ Write  ]  [Extd Part]
                              Return to main menu


```
Only these left?  :confused:  This is certainly not right. I quit.

---

### Post by adummy on 2010-10-08
any insight yet?

---

### Post by adummy on 2010-10-08
Quick update:

Did ```
 **sfdisk /dev/sdc < parts.txt**
``` as suggested here:
[http://www.rodsbooks.com/missing-parts/](http://www.rodsbooks.com/missing-parts/)

Now GParted can recognize the partitions, but the disk still won't boot. Still the ```
grub rescue>
``` prompt.

---

### Post by drs305 on 2010-10-08
If we have now switched to strictly a boot issue, please run the boot info script found in the following link. Posting the contents of RESULTS.txt will give us a good idea of what is happening so we can offer valid solutions.

When you copy the contents, please place them between "code" tags.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by adummy on 2010-10-08
> **drs305 said:**
> If we have now switched to strictly a boot issue, please run the boot info script found in the following link. Posting the contents of RESULTS.txt will give us a good idea of what is happening so we can offer valid solutions.

When you copy the contents, please place them between "code" tags.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)


Here we go: sda is the problematic hard disk. sdc and sdd are just two USB keys - one to boot and one to save data. Thanks!

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    59,538,062    59,538,000   7 HPFS/NTFS
/dev/sda2          59,552,955    90,269,234    30,716,280   7 HPFS/NTFS
/dev/sda3          90,269,694   182,418,074    92,148,381   f W95 Ext d (LBA)
/dev/sda5         131,328,000   182,418,074    51,090,075   7 HPFS/NTFS
/dev/sda6          90,269,696   125,583,359    35,313,664  83 Linux
/dev/sda7         125,585,408   127,217,663     1,632,256  82 Linux swap / Solaris
/dev/sda4         182,418,075   195,366,464    12,948,390   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4005 MB, 4005560320 bytes
16 heads, 32 sectors/track, 15280 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     7,823,359     7,823,328   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 16.0 GB, 16001036288 bytes
32 heads, 63 sectors/track, 15501 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    31,250,015    31,249,953   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        463E7D6A7359CE4B                       ntfs                                     
/dev/sda2        D652F41C52F402D3                       ntfs       XP                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        2C88743C8874071C                       ntfs       PRESARIO_RP                   
/dev/sda5        92E4DB1BE4DB0101                       ntfs       Home                          
/dev/sda6        0cb28e51-3a32-49ed-9a0f-6108868b63ab   ext4                                     
/dev/sda7        247b70ea-0c44-4fb5-844a-344597d80b6c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        CC6F-B660                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        617C-0466                              vfat       KINGSTON                      
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 463e7d6a7359ce4b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=247b70ea-0c44-4fb5-844a-344597d80b6c none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  57.1GB: boot/grub/core.img
  50.7GB: boot/grub/grub.cfg
  57.1GB: boot/initrd.img-2.6.32-24-generic
  57.3GB: boot/initrd.img-2.6.32-25-generic
  57.1GB: boot/vmlinuz-2.6.32-24-generic
  57.1GB: boot/vmlinuz-2.6.32-25-generic
  57.3GB: initrd.img
  57.1GB: initrd.img.old
  57.1GB: vmlinuz
  57.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
00000010  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000020  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
00000030  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000040  2c 30 30 2c 30 30 2c 30  30 2c 30 30 2c 30 30 2c  |,00,00,00,00,00,|
00000050  30 30 2c 30 31 2c 30 31  2c 30 31 2c 37 37 2c 39  |00,01,01,01,77,9|
00000060  38 2c 37 33 2c 34 44 2c  46 46 2c 35 32 2c 33 45  |8,73,4D,FF,52,3E|
00000070  2c 32 39 2c 5c 0d 0a 20  20 46 46 2c 30 31 2c 30  |,29,\..  FF,01,0|
00000080  31 2c 30 31 2c 42 31 2c  30 31 2c 30 31 2c 30 31  |1,01,B1,01,01,01|
00000090  2c 32 37 2c 30 31 2c 30  31 2c 30 31 2c 30 36 2c  |,27,01,01,01,06,|
000000a0  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
000000b0  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
000000c0  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
000000d0  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
000000e0  2c 30 30 2c 30 30 2c 30  30 2c 30 30 2c 30 30 2c  |,00,00,00,00,00,|
000000f0  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
00000100  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000110  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
00000120  30 2c 30 31 2c 30 31 2c  30 31 2c 35 46 2c 30 31  |0,01,01,01,5F,01|
00000130  2c 30 31 2c 30 31 2c 38  37 2c 30 31 2c 30 31 2c  |,01,01,87,01,01,|
00000140  30 31 2c 32 45 2c 30 31  2c 30 31 2c 30 31 2c 30  |01,2E,01,01,01,0|
00000150  37 2c 30 31 2c 30 31 2c  30 31 2c 30 31 2c 30 30  |7,01,01,01,01,00|
00000160  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
00000170  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000180  2c 30 30 2c 30 30 2c 30  30 2c 30 30 2c 30 30 2c  |,00,00,00,00,00,|
00000190  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
000001a0  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
000001b0  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 00 fe  |,00,\..  00,00..|
000001c0  ff ff 07 fe ff ff 02 80  72 02 9b 92 0b 03 00 fe  |........r.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 80 72 02 00 00  |............r...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 
```

---

### Post by drs305 on 2010-10-08
It appears Grub is looking for the Grub files on sda7 instead of sda6.

You should be able to boot from the Grub menu. 

First, press "c" to get to the grub prompt. Type:
set prefix=(hd0,6)/boot/grub
set root=(hd0,6)

ESC, then highlight the first entry and ENTER. If it boots to your normal installation, run "sudo update-grub"

If that doesn't work boot to the LiveCD desktop and run these commands:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

```

---

### Post by adummy on 2010-10-08
> **drs305 said:**
> It appears Grub is looking for the Grub files on sda7 instead of sda6.

You should be able to boot from the Grub menu. 

First, press "c" to get to the grub prompt. Type:
set prefix=(hd0,6)/boot/grub
set root=(hd0,6)

ESC, then highlight the first entry and ENTER.

If that doesn't work (or you are already on the LiveCD desktop), boot to the LiveCD desktop and run these commands:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
sudo update-grub
```

Thanks! So much for the UUIDs I guess.

The last line gave an error:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

``` 

Should I run boot script again?
Thanks!

---

### Post by drs305 on 2010-10-08
> **adummy said:**
> Thanks! So much for the UUIDs I guess.

The last line gave an error:
```

ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

``` 

Should I run boot script again?
Thanks!

The update-grub won't work if you are on the LiveCD and haven't rebooted. The command would only work if you had altered the Grub menu and then booted into your normal install first. I should have noted not to run it if you were on the LiveCD and will remove it in case someone else reviews this thread.

In theory the search line should have identified the UUIDs and corrected things, but apparently it didn't.

---

### Post by adummy on 2010-10-08
I ran the boot script again it looked almost identical. All the references to (0,7) are still there. I will try reboot now.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    59,538,062    59,538,000   7 HPFS/NTFS
/dev/sda2          59,552,955    90,269,234    30,716,280   7 HPFS/NTFS
/dev/sda3          90,269,694   182,418,074    92,148,381   f W95 Ext d (LBA)
/dev/sda5         131,328,000   182,418,074    51,090,075   7 HPFS/NTFS
/dev/sda6          90,269,696   125,583,359    35,313,664  83 Linux
/dev/sda7         125,585,408   127,217,663     1,632,256  82 Linux swap / Solaris
/dev/sda4         182,418,075   195,366,464    12,948,390   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4005 MB, 4005560320 bytes
16 heads, 32 sectors/track, 15280 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     7,823,359     7,823,328   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 16.0 GB, 16001036288 bytes
32 heads, 63 sectors/track, 15501 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63    31,250,015    31,249,953   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        463E7D6A7359CE4B                       ntfs                                     
/dev/sda2        D652F41C52F402D3                       ntfs       XP                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        2C88743C8874071C                       ntfs       PRESARIO_RP                   
/dev/sda5        92E4DB1BE4DB0101                       ntfs       Home                          
/dev/sda6        0cb28e51-3a32-49ed-9a0f-6108868b63ab   ext4                                     
/dev/sda7        247b70ea-0c44-4fb5-844a-344597d80b6c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        CC6F-B660                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        617C-0466                              vfat       KINGSTON                      
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6        /mnt                     ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 463e7d6a7359ce4b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=247b70ea-0c44-4fb5-844a-344597d80b6c none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  57.1GB: boot/grub/core.img
  50.7GB: boot/grub/grub.cfg
  57.1GB: boot/initrd.img-2.6.32-24-generic
  57.3GB: boot/initrd.img-2.6.32-25-generic
  57.1GB: boot/vmlinuz-2.6.32-24-generic
  57.1GB: boot/vmlinuz-2.6.32-25-generic
  57.3GB: initrd.img
  57.1GB: initrd.img.old
  57.1GB: vmlinuz
  57.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
00000010  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000020  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
00000030  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000040  2c 30 30 2c 30 30 2c 30  30 2c 30 30 2c 30 30 2c  |,00,00,00,00,00,|
00000050  30 30 2c 30 31 2c 30 31  2c 30 31 2c 37 37 2c 39  |00,01,01,01,77,9|
00000060  38 2c 37 33 2c 34 44 2c  46 46 2c 35 32 2c 33 45  |8,73,4D,FF,52,3E|
00000070  2c 32 39 2c 5c 0d 0a 20  20 46 46 2c 30 31 2c 30  |,29,\..  FF,01,0|
00000080  31 2c 30 31 2c 42 31 2c  30 31 2c 30 31 2c 30 31  |1,01,B1,01,01,01|
00000090  2c 32 37 2c 30 31 2c 30  31 2c 30 31 2c 30 36 2c  |,27,01,01,01,06,|
000000a0  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
000000b0  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
000000c0  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
000000d0  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
000000e0  2c 30 30 2c 30 30 2c 30  30 2c 30 30 2c 30 30 2c  |,00,00,00,00,00,|
000000f0  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
00000100  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000110  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
00000120  30 2c 30 31 2c 30 31 2c  30 31 2c 35 46 2c 30 31  |0,01,01,01,5F,01|
00000130  2c 30 31 2c 30 31 2c 38  37 2c 30 31 2c 30 31 2c  |,01,01,87,01,01,|
00000140  30 31 2c 32 45 2c 30 31  2c 30 31 2c 30 31 2c 30  |01,2E,01,01,01,0|
00000150  37 2c 30 31 2c 30 31 2c  30 31 2c 30 31 2c 30 30  |7,01,01,01,01,00|
00000160  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
00000170  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000180  2c 30 30 2c 30 30 2c 30  30 2c 30 30 2c 30 30 2c  |,00,00,00,00,00,|
00000190  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
000001a0  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
000001b0  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 00 fe  |,00,\..  00,00..|
000001c0  ff ff 07 fe ff ff 02 80  72 02 9b 92 0b 03 00 fe  |........r.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 80 72 02 00 00  |............r...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 


```

---

### Post by drs305 on 2010-10-08
The grub-install doesn't create a new grub.cfg, so Grub is still going to look for sda7 and the boot will probably fail.

I'll post this quickly and hopefully catch you first, then elaborate.

Just tell me how you got to the Desktop - modifying the menu or using the LiveCD.

A. If you booted to the LiveCD, we will chroot to update-grub:
```

sudo mkdir /mnt/temp
sudo mount /dev/sda6 /mnt/temp && sudo mount -B /dev /mnt/temp/dev && sudo mount -B /proc /mnt/temp/proc && sudo mount -B /sys /mnt/temp/sys && sudo mount -B /dev/pts /mnt/temp/dev/pts && sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf && sudo chroot /mnt/temp

```
You will now be in a chroot environment and should have a "root" prompt.
Now you can update grub (sudo is not required):
```
update-grub
exit

```

B. If you altered the Grub menu before booting and are now in your normal install:
```
sudo update-grub
```
Run the boot info script. If it's still showing (hd0,7), then we will forcefully change the grub entry:
```
sudo chmod +w /boot/grub/grub.cfg
gksu gedit /boot/grub/grub.cfg
```
Find the first menuentry and manually change it to "**set root=(hd0,6)**" and save the file. 

In either case, you can run the info script and it should show (hd0,6) for the root address of the menuentry.
> 
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,**[COLOR="DarkRed"]6[/COLOR]**)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}


---

### Post by srs5694 on 2010-10-08
I know you're past this point, but just to provide the background information, the reason GParted didn't see the disk is almost certainly that there was corrupt data for a /dev/sda8 partition on the disk. (Perhaps that was one that you deleted in your earlier changes, but the deletion went awry for some reason.) Saving the partition table from fdisk would have fixed this; the sfdisk command you used did the job, too. The only drawback to this fix is that the partition is now gone -- but it sounds like it was probably not wanted anyhow, so that's no big deal.

This mucking about may have disrupted the partition order, which is why GRUB is now acting up. There are various ways to re-install GRUB. The approach I favor (and this is admittedly a rather vague overview) is to use [Super GRUB Disk](http://www.supergrubdisk.org/) or something similar to get your regular disk-based installation booted, and then type "sudo update-grub" and then "sudo grub-install /dev/sda". This should update your GRUB boot-time configuration file (/boot/grub/grub.cfg) and then update the GRUB code in the MBR.

One warning: Because your partition table entries are out of order, it's conceivable they'll change if/when you make further changes to your partition table. If this happens, you'll have to update GRUB and re-install it once more. It looks like you've got free space between the swap partition (/dev/sda7) and the NTFS partition (/dev/sda5) and after the NTFS partition (/dev/sda5). If you plan to make any changes, you might want to make them now, and then sort the partition table entries using the 'f' option on the fdisk experts' menu. Once you've done this, re-install GRUB 2. (I'm not sure if a reboot will be required between sorting the partitions and re-installing GRUB 2.)

---

### Post by adummy on 2010-10-08
Wow it worked! Thanks so much! :)

I still wonder why the UUIDs didn't work. Does that mean every time I change the partitions I will break the grub?

Now back to the original issue: I got a blank screen saying not enough swap space and the system just hung. After force shut down and restarting I deleted an unused partition to make room for more swap space. I did that with Disk Utilities since GParted wasn't available in the installed ubuntu. But Disk Utilities failed to generate a new swap space partition. Thus the change of sda numbers. So what is the correct way to make more room for the swap? The free space is right next to the current swap partition so ideally I would just grow the size of the current swap but I don't know how. Thanks!

---

### Post by adummy on 2010-10-08
Sorry I missed this post earlier. I guess our posts crossed.

> **drs305 said:**
> The grub-install doesn't create a new grub.cfg, so Grub is still going to look for sda7 and the boot will probably fail.


I thought so too but it just worked like magic. :)

> 
I'll post this quickly and hopefully catch you first, then elaborate.

Just tell me how you got to the Desktop - modifying the menu or using the LiveCD.



It's a USB key so I suppose it's LiveCD equivalent?

> 

A. If you booted to the LiveCD, we will chroot to update-grub:
```

sudo mkdir /mnt/temp
sudo mount /dev/sda6 /mnt/temp && sudo mount -B /dev /mnt/temp/dev && sudo mount -B /proc /mnt/temp/proc && sudo mount -B /sys /mnt/temp/sys && sudo mount -B /dev/pts /mnt/temp/dev/pts && sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf && sudo chroot /mnt/temp

```You will now be in a chroot environment and should have a "root" prompt.
Now you can update grub (sudo is not required):
```
update-grub
exit

```B. If you altered the Grub menu before booting and are now in your normal install:
```
sudo update-grub
```Run the boot info script. If it's still showing (hd0,7), then we will forcefully change the grub entry:
```
sudo chmod +w /boot/grub/grub.cfg
gksu gedit /boot/grub/grub.cfg
```Find the first menuentry and manually change it to "**set root=(hd0,6)**" and save the file. 

In either case, you can run the info script and it should show (hd0,6) for the root address of the menuentry.

Here is the result of the script. It still has a bunch of (hd0,7). 


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    59,538,062    59,538,000   7 HPFS/NTFS
/dev/sda2          59,552,955    90,269,234    30,716,280   7 HPFS/NTFS
/dev/sda3          90,269,694   182,418,074    92,148,381   f W95 Ext d (LBA)
/dev/sda5         131,328,000   182,418,074    51,090,075   7 HPFS/NTFS
/dev/sda6          90,269,696   125,583,359    35,313,664  83 Linux
/dev/sda7         125,585,408   127,217,663     1,632,256  82 Linux swap / Solaris
/dev/sda4         182,418,075   195,366,464    12,948,390   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 16.0 GB, 16001036288 bytes
32 heads, 63 sectors/track, 15501 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    31,250,015    31,249,953   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        463E7D6A7359CE4B                       ntfs                                     
/dev/sda2        D652F41C52F402D3                       ntfs       XP                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4        2C88743C8874071C                       ntfs       PRESARIO_RP                   
/dev/sda5        92E4DB1BE4DB0101                       ntfs       Home                          
/dev/sda6        0cb28e51-3a32-49ed-9a0f-6108868b63ab   ext4                                     
/dev/sda7        247b70ea-0c44-4fb5-844a-344597d80b6c   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdc1        617C-0466                              vfat       KINGSTON                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/KINGSTON          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 463e7d6a7359ce4b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda4)" {
    insmod ntfs
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=247b70ea-0c44-4fb5-844a-344597d80b6c none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  57.1GB: boot/grub/core.img
  50.7GB: boot/grub/grub.cfg
  57.1GB: boot/initrd.img-2.6.32-24-generic
  57.3GB: boot/initrd.img-2.6.32-25-generic
  57.1GB: boot/vmlinuz-2.6.32-24-generic
  57.1GB: boot/vmlinuz-2.6.32-25-generic
  57.3GB: initrd.img
  57.1GB: initrd.img.old
  57.1GB: vmlinuz
  57.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
00000010  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000020  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
00000030  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000040  2c 30 30 2c 30 30 2c 30  30 2c 30 30 2c 30 30 2c  |,00,00,00,00,00,|
00000050  30 30 2c 30 31 2c 30 31  2c 30 31 2c 37 37 2c 39  |00,01,01,01,77,9|
00000060  38 2c 37 33 2c 34 44 2c  46 46 2c 35 32 2c 33 45  |8,73,4D,FF,52,3E|
00000070  2c 32 39 2c 5c 0d 0a 20  20 46 46 2c 30 31 2c 30  |,29,\..  FF,01,0|
00000080  31 2c 30 31 2c 42 31 2c  30 31 2c 30 31 2c 30 31  |1,01,B1,01,01,01|
00000090  2c 32 37 2c 30 31 2c 30  31 2c 30 31 2c 30 36 2c  |,27,01,01,01,06,|
000000a0  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
000000b0  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
000000c0  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
000000d0  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
000000e0  2c 30 30 2c 30 30 2c 30  30 2c 30 30 2c 30 30 2c  |,00,00,00,00,00,|
000000f0  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
00000100  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000110  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
00000120  30 2c 30 31 2c 30 31 2c  30 31 2c 35 46 2c 30 31  |0,01,01,01,5F,01|
00000130  2c 30 31 2c 30 31 2c 38  37 2c 30 31 2c 30 31 2c  |,01,01,87,01,01,|
00000140  30 31 2c 32 45 2c 30 31  2c 30 31 2c 30 31 2c 30  |01,2E,01,01,01,0|
00000150  37 2c 30 31 2c 30 31 2c  30 31 2c 30 31 2c 30 30  |7,01,01,01,01,00|
00000160  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 2c 30  |,00,\..  00,00,0|
00000170  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
00000180  2c 30 30 2c 30 30 2c 30  30 2c 30 30 2c 30 30 2c  |,00,00,00,00,00,|
00000190  30 30 2c 30 30 2c 30 30  2c 30 30 2c 30 30 2c 30  |00,00,00,00,00,0|
000001a0  30 2c 30 30 2c 30 30 2c  30 30 2c 30 30 2c 30 30  |0,00,00,00,00,00|
000001b0  2c 30 30 2c 5c 0d 0a 20  20 30 30 2c 30 30 00 fe  |,00,\..  00,00..|
000001c0  ff ff 07 fe ff ff 02 80  72 02 9b 92 0b 03 00 fe  |........r.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 80 72 02 00 00  |............r...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 


```

---

### Post by drs305 on 2010-10-08
I guess the secret then is to make sure you run "sudo update-grub" once you have completed a normal boot from the Grub2 menu. That should update everything to match what you system currently thinks it has. For now, I would say the UUIDs *are* working, as I think at the moment your "search" line UUIDs are overriding the erroneous "set root" command above it. From the first part of the RESULTS.txt you can see that Grub is on the MBR and properly looking to sda6 for it's files, which was the original problem.

Before you do, you might want to make a backup copy of grub.cfg somewhere and you could even take your existing/working menuentry and copy it into /etc/grub.d/40_custom. After you save 40_custom and run update-grub you will have an extra copy of the 'working' menuentry. It doesn't get updated but for now it might be a good 'insurance' entry on your grub menu. You can always remove it once everything seems back to normal.

---

### Post by adummy on 2010-10-08
Sorry I hope this is not too confusing. Since the posts crossed I have not applied the most recent suggestions yet. Now I am inside Desktop from a "normal" hard disk boot. Do I still need to fix the (hd0,7) stuff?

I also still need help to enlarge the swap partition as detailed two posts earlier. Thanks! :)

---

### Post by adummy on 2010-10-08
> **drs305 said:**
> I guess the secret then is to make sure you run "sudo update-grub" once you have completed a normal boot from the Grub2 menu. That should update everything to match what you system currently thinks it has. For now, I would say the UUIDs *are* working, as I think at the moment your "search" line UUIDs are overriding the erroneous "set root" command above it. From the first part of the RESULTS.txt you can see that Grub is on the MBR and properly looking to sda6 for it's files, which was the original problem.

Before you do, you might want to make a backup copy of grub.cfg somewhere and you could even take your existing/working menuentry and copy it into /etc/grub.d/40_custom. After you save 40_custom and run update-grub you will have an extra copy of the 'working' menuentry. It doesn't get updated but for now it might be a good 'insurance' entry on your grub menu. You can always remove it once everything seems back to normal.

Sorry the posts keeps crossing. I now copied the grub.cfg and pasted into a USB key. I also found the 40_custom file. Did you mean I edit it with a text editor? Where is my menuentry? The entire content of grub.cfg?

---

### Post by drs305 on 2010-10-08
> **adummy said:**
> Sorry I hope this is not too confusing. Since the posts crossed I have not applied the most recent suggestions yet. Now I am inside Desktop from a "normal" hard disk boot. Do I still need to fix the (hd0,7) stuff?

I also still need help to enlarge the swap partition as detailed two posts earlier. Thanks! :)

We keep simul-posting. My response to this post is ... the previous post!

---

### Post by drs305 on 2010-10-08
> **adummy said:**
> Sorry the posts keeps crossing. I now copied the grub.cfg and pasted into a USB key. I also found the 40_custom file. Did you mean I edit it with a text editor? Where is my menuentry? The entire content of grub.cfg?

No, you would copy only the menuentry, which starts with "menuentry" and ends with a single [B]}}/B]. 

This is what you would copy. In fact, I would put one for sda6 and one for sda7. If one doesn't work the other one probably will. ;-)  You can put anything you want in the title (between the ' ' ).
> 
menuentry 'Ubuntu - sda6, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}

menuentry 'Ubuntu - sda7 , with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 0cb28e51-3a32-49ed-9a0f-6108868b63ab
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0cb28e51-3a32-49ed-9a0f-6108868b63ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}


---

### Post by srs5694 on 2010-10-08
The reason GRUB was failing, judging by the Boot Info Script output, is that the GRUB code *in the MBR* was referring to /dev/sda6:

> ```

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

```

Backing up a bit, GRUB exists in several places. Precisely where varies from one installation to another and from one version of GRUB to another, but the locations can include the MBR, unallocated sectors after the MBR (on MBR disks only), a special BIOS Boot Partition (on GPT disks only), the boot sector of a Linux or other boot partition, files in the Linux root (/) or /boot partition, and files in /etc. *Some* of these locations can use UUID references, but others can't. In particular, the earliest GRUB code, in the MBR, must be extremely compact, and AFAIK it can't refer to anything by UUID; it uses partition numbers or even sector numbers.

As to how to deal with growing the swap space, I would recommend using a live CD or an emergency disc. Launch GParted from this, disable swap space (if necessary), and either grow the swap partition or delete it and create a new swap partition. If you delete and re-create the swap space, though, you're likely to have to edit /etc/fstab when you reboot so that it refers to the correct swap partition.

Backing up a bit, though, it's very unusual for a Linux installation on a modern computer to run out of swap space. Modern computers, with 2 GiB or more of RAM, seldom need to make significant use of swap space. Even a system with just 1 GiB of RAM is unlikely to need so much more that you'll run out of swap space. If you've got particularly little RAM, you might be legitimately running out. Likewise if you're running some particularly memory-hungry application. If you don't think this is the case, though, you might want to post information on your system. Typing "free -m" and posting the results between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings will provide most of the information needed to diagnose this information. Typing "swapon -i" and posting that might be useful, too. You could also type "top", then type "M" in the utility. That will produce a list of running applications, sorted by memory used (the "%MEM" column). This will make it easy to spot any memory hogs. Post those results if you need help interpreting them.

---

### Post by adummy on 2010-10-08
> **drs305 said:**
> No, you would copy only the menuentry, which starts with "menuentry" and ends with a single [B]}}/B]. 

This is what you would copy. In fact, I would put one for sda6 and one for sda7. If one doesn't work the other one probably will. ;-)  You can put anything you want in the title (between the ' ' ).

Almost there ... What's the correct way to edit 40_custom? I am spoiled by GUI editor like gedit and it won't let me edit because I don't own the file.

---

### Post by drs305 on 2010-10-08
Actually, you have to go back to the first RESULTS.txt in Post #19. In that post the RESULTS.txt indicates that Grub was looking at sda7 and sda7 was a swap partition. 

Now the MBR points to sda6, which is where the Grub2 files are located. The UUIDs also point to sda6 but for some reason 'root' continues to point to sda7. Since 'search' will set the root partition, it overrides the line before it and correctly points to the correct partition just before the linux line is executed.

---

### Post by drs305 on 2010-10-08
> **adummy said:**
> Almost there ... What's the correct way to edit 40_custom? I am spoiled by GUI editor like gedit and it won't let me edit because I don't own the file.

Edit it as root:
```

gksudo gedit /etc/grub.d/40_custom

```

Any file owned by root (system files) can't be edited by a normal user until you use "sudo" for a terminal command or app such as *nano* or *update-grub*; use "gksu" or "gksudo" for GUI apps.

There is a GUI way to do it as well. You can install *nautilus-gksu*. Then in a file browser, you would navigate to /etc/grub.d/, right click the file and select "Open as Administrator".

---

### Post by adummy on 2010-10-08
> **drs305 said:**
> Edit it as root:
```

gksudo gedit /etc/grub.d/40_custom

```Any file owned by root (system files) can't be edited by a normal  user until you use "sudo" for a terminal command or app such as *nano* or *update-grub*; use "gksu" or "gksudo" for GUI apps.

There is a GUI way to do it as well. You can install *nautilus-gksu*. Then in a file browser, you would navigate to /etc/grub.d/, right click the file and select "Open as Administrator".

Thanks for the hint! I just finished editing and ran update-grub. Looks like the grub.cfg now has (hd0,6) instead of (hd0,7), and the menuentries appended at the end of the file. Sounds good I suppose? I restarted and it booted OK. :) Now to tackle the swap space:

> **srs5694 said:**
> The reason GRUB was failing, judging by the Boot Info Script output, is that the GRUB code *in the MBR* was referring to /dev/sda6:



Backing up a bit, GRUB exists in several places. Precisely where varies from one installation to another and from one version of GRUB to another, but the locations can include the MBR, unallocated sectors after the MBR (on MBR disks only), a special BIOS Boot Partition (on GPT disks only), the boot sector of a Linux or other boot partition, files in the Linux root (/) or /boot partition, and files in /etc. *Some* of these locations can use UUID references, but others can't. In particular, the earliest GRUB code, in the MBR, must be extremely compact, and AFAIK it can't refer to anything by UUID; it uses partition numbers or even sector numbers.

As to how to deal with growing the swap space, I would recommend using a live CD or an emergency disc. Launch GParted from this, disable swap space (if necessary), and either grow the swap partition or delete it and create a new swap partition. If you delete and re-create the swap space, though, you're likely to have to edit /etc/fstab when you reboot so that it refers to the correct swap partition.

Backing up a bit, though, it's very unusual for a Linux installation on a modern computer to run out of swap space. Modern computers, with 2 GiB or more of RAM, seldom need to make significant use of swap space. Even a system with just 1 GiB of RAM is unlikely to need so much more that you'll run out of swap space. If you've got particularly little RAM, you might be legitimately running out. Likewise if you're running some particularly memory-hungry application. If you don't think this is the case, though, you might want to post information on your system. Typing "free -m" and posting the results between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings will provide most of the information needed to diagnose this information. Typing "swapon -i" and posting that might be useful, too. You could also type "top", then type "M" in the utility. That will produce a list of running applications, sorted by memory used (the "%MEM" column). This will make it easy to spot any memory hogs. Post those results if you need help interpreting them.

I thought the 3GB RAM the notebook has are plenty. I am trying to remember what was running. I think NetBeans, Fluid, BeyondCompare, gedit, (coming from the Windows world I am spoiled by GUIs), Firefox with maybe 7 or 8 tabs, some File Browsers and Terminals, and a GPS software tangoGPS. If I keep running into the same problem I will post. In the mean time I will use System Monitor to watch the memory usage.

Going on to try GParted on the swap space...

---

### Post by adummy on 2010-10-08
> **adummy said:**
> ....

Going on to try GParted on the swap space...

Worked on 2nd try. The first time it complaints about overlapping partitions. So I made it slightly smaller and that worked. Thanks everyone! :)

---

