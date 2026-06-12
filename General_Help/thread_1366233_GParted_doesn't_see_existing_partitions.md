---
title: "GParted doesn't see existing partitions"
date: 2009-12-28
forum: General Help
---

### Post by Coco999 on 2009-12-28
GParted doesn't see existing partitions, while "Lugares" (places, locations?) report them (only the fate32 ones). As a consequence, I can't install Ubuntu to the hard disk. I have partitioned my disk into 4 fat32 partitions and have left on purpose 20 GB not assigned, hoping to install Ubuntu to it. I may be doing something wrong, but can't figure what it is. Please help me. Thank you in advance

---

### Post by QrK0 on 2009-12-28
You should see the 20G as unallocated space, beacuse there is no partition there.
Anyway, did you try to start the livecd session and look the partitions with Gparted?

---

### Post by Coco999 on 2009-12-28
You say

> You should see the 20G as unallocated space, beacuse there is no partition there.
Anyway, did you try to start the livecd session and look the partitions with Gparted?

GParted shows all of the HD as unallocated space, this is my trouble.

---

### Post by QrK0 on 2009-12-28
And how many primary partitions have the disk?
Can you show the result of:
```
$ sudo fdisk -l
```?

---

### Post by Mahngiel on 2009-12-28
If you are using a single HDD, and those 4 Fat32 formatted partitions are all Primary Partitions, then you won't be able to install anyways.  A HDD is limited to 4 primary partitions, one of which can house a host of Logical Partitions.  

Not exactly sure why you've 4 Fat32 partitions anyhow, most systems use the Ext3 or 4 formatting scheme, and Windows uses NTFS since Windows NT.  But i'm not one to tell you what to do.  

As far as not being able to see your partitions with GParted, perhaps you haven't selected the correct disk.  On the right hand corner is a dialog box which is actually a drop-down menu if you click it.  Perhaps that is your issue at hand.

---

### Post by Coco999 on 2009-12-29
This is the result:

[FONT="Courier New"]> ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x00000001

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/sda2            3825       16827   104446597+   5  Extendida
/dev/sda3            7012       10835    30716280    b  W95 FAT32
/dev/sda5            3825        7011    25599514+   b  W95 FAT32
/dev/sda6           10836       16827    48130708+   b  W95 FAT32
ubuntu@ubuntu:~$[/FONT]


I have only one primary partition: /dev/sda1
/dev/sda2 is an extended partition divided into 3 logical ones.
I left on purpose an unallocated space of 20 GB to allow for Ubuntu to install itself in it. This would be the smart thing to do, but Ubuntu doesn't seem to realize it and there is no way for me to force this.

As to the choice of FAT32 instead of NTFS (both accepted by Windows XP), I did it because some versions of Linux could not read NTFS. Probably Ubuntu can now, but I've followed my old use.

My problem is not actually GParted, but the difficulty to install Ubuntu to the hard disk. By the way, I have only one HD. I have edited the title to show this.

Thank you for your help.

---

### Post by QrK0 on 2009-12-29
This seems the "missing" partition...

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)
```

I think this is due to a problem in the partition table.
And beacuse there are error on the partition table, Gparted don't show the partitions.

Probably you need to reformat the disk (loosing all the info stored!)

---

### Post by dandnsmith on 2009-12-29
> **Coco999 said:**
> 
I have only one primary partition: /dev/sda1
/dev/sda2 is an extended partition divided into 3 logical ones.
I left on purpose an unallocated space of 20 GB to allow for Ubuntu to install itself in it. This would be the smart thing to do, but Ubuntu doesn't seem to realize it and there is no way for me to force this.

As to the choice of FAT32 instead of NTFS (both accepted by Windows XP), I did it because some versions of Linux could not read NTFS. Probably Ubuntu can now, but I've followed my old use.

My problem is not actually GParted, but the difficulty to install Ubuntu to the hard disk. By the way, I have only one HD. I have edited the title to show this.

I think the real problem is that you've left the empty space after the extended partition - which isn't 'usual'.

2 tactics suggest themselves:
a) create a partition after the end of that extended partition for ubuntu - because you 'need' space for swap as well, this might not be the best solution to try for (I'm not sure that you could create a 2nd extended partition, and split that)

b) extend the extended partition to fill the HDD, and then create partitions for Ubuntu within that. I think gparted will allow this (but am not sure, having not tried it out).

HTH

---

### Post by Coco999 on 2009-12-29
> I think this is due to a problem in the partition table.
And beacuse there are error on the partition table, Gparted don't show the partitions.

Probably you need to reformat the disk (loosing all the info stored!)

You may be right in this. In preliminary tests, I had seen the partitions in GParted, but something may have happened that corrupted the partition table. Your suggestion looks like a brute force solution. I have a lot inside that disk that took me many hours of toil. Isn't there a way to repair or edit the partition table?


> 2 tactics suggest themselves:
a) create a partition after the end of that extended partition for ubuntu - because you 'need' space for swap as well, this might not be the best solution to try for (I'm not sure that you could create a 2nd extended partition, and split that)


That's precisely where I left the unallocated space, after the extended partition. I think I could create a 2nd ext. part. in this space, provided I could use GParted, which I can't because of the trouble in the part. table.

> b) extend the extended partition to fill the HDD, and then create partitions for Ubuntu within that. I think gparted will allow this (but am not sure, having not tried it out).

I think I could extend the extended partition to use up the unallocated space, but I don't know how to create partitions for Ubuntu. Same trouble as before, I can't use GParted until I find a way to repair the partition table,

---

### Post by oldfred on 2009-12-29
You only can have one extended partition. What seems strange in you partitions is normally sda1-4 numbers are for primary and sda5 & up are for logical inside the primary. Any of the sda1-4 can be the extended but if you create a primary it can lock the extended. But you have an ext3 inside the extended partition.

I cannot recommend FAT any more. Three years ago I set up a shared FAT partition for windows and Ubuntu because 3 years ago the reading of NTFS was not quite 100%. Now reading & writing NTFS is consided very good from Ubuntu.

NTFS and Fat info:
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by rahilm on 2009-12-29
See if this solves ur problem..if u r having d same  i had,
[http://ubuntuforums.org/showthread.php?t=1342870](http://ubuntuforums.org/showthread.php?t=1342870)

---

### Post by dandnsmith on 2009-12-29
> **Coco999 said:**
> You may be right in this. In preliminary tests, I had seen the partitions in GParted, but something may have happened that corrupted the partition table. Your suggestion looks like a brute force solution. I have a lot inside that disk that took me many hours of toil. Isn't there a way to repair or edit the partition table?

I've used fdisk in the past. Unfortunately, for this sort of manoeuvre, you need to get to the command line. You'll also want to be doing it without the partitions mounted.

I commend not only fdisk, but also sfdisk to your attention. By taking care, and recording the details of the partition table, you can delete any or all of the partition entries, and then recreate them - you need the start point, end point and partition ID for each. Since they are usually created to start and end on a cylinder boundary, you don't (necessarily) need the number of blocks.

> That's precisely where I left the unallocated space, after the extended partition. I think I could create a 2nd ext. part. in this space, provided I could use GParted, which I can't because of the trouble in the part. table.
I don't really recommend trying to make a second extended partition.

> I think I could extend the extended partition to use up the unallocated space, but I don't know how to create partitions for Ubuntu. Same trouble as before, I can't use GParted until I find a way to repair the partition table,

For the main file partitions you need 'linux' partition ID, and for swap the swap ID - fdisk gives all the help need for this.

If you follow this work with the Ubuntu install, then the manual method of picking the partitions is the one to use, and remember to format them appropropriately.


Good luck

---

### Post by QrK0 on 2009-12-29
> **Coco999 said:**
> You may be right in this. In preliminary tests, I had seen the partitions in GParted, but something may have happened that corrupted the partition table. Your suggestion looks like a brute force solution. I have a lot inside that disk that took me many hours of toil. Isn't there a way to repair or edit the partition table?
My suggestion is to not touch the partitions anymore, at  least before you repair them and recovers the data.
Once you have the existing data in a safe place (usb, dvd...), then you can try to play again with the partitions.
There are lot of (free) recovery partitions software, just ask google

---

### Post by oldfred on 2009-12-29
You can use testdisk to repair partitions and recover data in most cases. Testdisk is on most recovery CDs and is in the repositories.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Using sfdisk to fix partition table problems
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
# The partition table is located at sectors 447--512 on the drive.
# A sector = 512 bytes.
Here is the specification of the partition table format:
[http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3](http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3)

---

### Post by mdmill9999 on 2009-12-29
The problem here is that gparted uses the (microsoft) partition tables in the master boot record of the drive, which is limited to 4 entries. [Extended partitions are more suseptible to irrecoverable damage because they daisy chain from one to another, and should perhaps be avoided].
 
If you really want complete flexibility I suggest becoming familiar with the Ranish Partition manager/ boot manager combo freeware (version 2.44). It is OS independant, and can allways be booted directly from diskette in an emergency. You create a special small partition at the end of the drive which holds the programs and an independant partition table limited to 31 partitions. During boot a small text window allows you to boot from any partition; or you can jump to the partition program at this time and create partitions; and select which partitions are to be written to the microsoft MBR partition table (and thus visible to the OS and other applications such as Gparted).
 
I currently have dos5, win3.1,w98,xppro, xphome,xphome duplicate(as backup), and linux ubuntu,kubuntu,open suse, and ubuntu2(for special testing), and three large data partitions, installed on my 500GB disk--and i am a relative novice at multi-booting. I can install and test new OS installations quickly with complete controll of the disk partitions. This is an extreme case of course, but it is nice to have the flexibility and control.
 
This is not a quick fix for you (or anyone else) because it takes time to get used to the program, which is powerfull, and can be confusing/destructive at first. A lot of reading is involved. You would want to start on a clean system and experiment.
 
For multibooters I believe this is the approach to take. Also BootitNG is a profesional program ($30+) which does the same thing probably better.
 
This does not solve your problem directly, but may be of interest [FYI]

---

### Post by Coco999 on 2009-12-30
Thanks to all of you who have helped me with your advise. I'm learning a lot, but feel far from getting the thing working. For instance, I was not aware of the partition table and scarcely know of the existance of the MBR. I have to study and test many things in order to arrive at something useful, always with the risk of loosing valuable information. Perhaps it is wiser for me to start again from scratch: backup and reformat the whole disk.

Therefore I'll state my requirements and request help to achieve them. My hard disk is 160 GB. My idea is to allow 20 GB for UBUNTU and 140 for Wxp, divided into a primary partition and an extended one (divided into 3 logical). If in addition I can allow some of the space for testing a third operating system, so much the better. Please help me to plan the partitions and the way to achieve them, perhaps with the live UBUNTU. I would also prefer to install first of all UBUNTU and then WXP, if it is possible.

Thanks again and best wishes for 2010.
Coco

---

### Post by frt975 on 2009-12-30
Try Wubi. You don't need a separate partition for it and it can be removed by simply going to Add/Remove Applications.

---

### Post by Coco999 on 2009-12-30
I tried Wubi and it seemed to be a beauty and the solution to my difficulties. But the first trouble is that it gave me no choice and started to download and install an amd64 version. I have Intel 32 bits. Second trouble is that a few minutes before finishing, it stopped with an error message.

If I do this sort of installation, may I still add in the future some software?

---

### Post by Jackzor on 2009-12-30
Format to ext3 or 4.. It should work

---

### Post by oldfred on 2009-12-31
I do not particularly recommend Wubi as it is somewhat like a LiveCD that you install inside your windows. It runs faster than the liveCD and allows updates. It is for windows users that want to try Ubuntu. But once you decide to use Ubuntu as least some of the time on a regular basis it is better to have a true dual boot.

It is generally easier to install windows first, then Ubuntu. I also like to have another NTFS partition to share data between the systems. Some windows users even recommend that data not be in the windows boot partition but in a separate data partition. 

Windows has to be on a primary partition. Data and Ubuntu do not have to be. I would use gparted to set up two NTFS partitions. One for windows and one for shared data. Then you can install Ubuntu in the remaining space.
APC various dual boot graphical install
[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

Windows7 install is somewhat different but the dual boot process is the same:
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)

---

### Post by dandnsmith on 2009-12-31
> **oldfred said:**
> It is generally easier to install windows first, then Ubuntu. I also like to have another NTFS partition to share data between the systems. Some windows users even recommend that data not be in the windows boot partition but in a separate data partition.
I'd go with the separate partition(s) for data - it sidesteps all sorts of problems when wishing to install/reinstall OSs.

> Windows has to be on a primary partition.
Windows doesn't always have to be on a primary partition (I have installations where it isn't), but it is certainly safer to plan on it being that way.
Linux based systems can be on logical partitions within extended partitions, as long as the bootloader can 'reach' them.

---

### Post by Coco999 on 2010-01-01
I finally achieved what I wanted. 9.10 is installed in the previously unallocated space, after a primary partition with windows and en extended partition (divided into 3 logical ones) with data.

At a point in the installation, you have to make a choice in a GParted view of your HD. GParted reported all of the HD as unallocated (due perhaps to my corrupt table of partitions). So I could not make this choice, but nevertheless proceeded with the installation. At the time I had a second HD connected to the system, that has a flawed Windows installed. Next time I tried, I had disconnected this 2nd disk, and found no evidence at all of Ubuntu.

But after connecting again the 2nd HD, upon starting up I had the joy to see the GRUB options list, for me to choose an operating system to boot, including UBUNTU and two Windows, the regular and the flawed ones.

At this point, I could close the thread as solved, but I still have some doubts.
1. How do I correct my table of partitions?
2. I would like to be able to remove that 2nd disk and still have access to my regular Windows + Ubuntu. This may involve at least altering the GRUB table. Is that so and how can I do?

Thank you very much to all for your enlightening help

---

### Post by oldfred on 2010-01-01
Did it actually install to your second hard drive? To see your entire configuration run this script with both drives installed. You do not need to use the liveCD if you can boot into your system, it will probably then download into the download directory on a working system where on the liveCD it downloads onto the desktop.

Boot Info Script 0.42 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by Coco999 on 2010-01-01
I reviewed the 2nd drive with mc and confirmed mi idea that Ubuntu is not installed there. By the way, mc was not within my Ubunto and I had to install it from the Web, a much more straightforward procedure than with Windows installations, a real beauty.

I proceeded as instructed and got this:


```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb5 starts at sector 61432686.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb6 starts at sector 174064338.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 112631715.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 80.0 GB, 80000000000 bytes
255 cabezas, 63 sectores/pista, 9726 cilindros, 156250000 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0xe24be24b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    24,579,449    24,579,387   c W95 FAT32 (LBA)
/dev/sda2          24,579,450   156,248,189   131,668,740   f W95 Ext d (LBA)
/dev/sda5          24,579,513    49,158,899    24,579,387   b W95 FAT32
/dev/sda6          49,158,963    73,738,349    24,579,387   7 HPFS/NTFS
/dev/sda7          73,738,413    98,317,799    24,579,387   7 HPFS/NTFS
/dev/sda8          98,317,863   144,135,179    45,817,317   b W95 FAT32
/dev/sda9         144,135,243   155,621,654    11,486,412  83 Linux
/dev/sda10        155,621,718   156,248,189       626,472  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________
omitiendo la partición vacía (5)

Disco /dev/sdb: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    61,432,559    61,432,497   c W95 FAT32 (LBA)
/dev/sdb2          61,432,560   270,325,754   208,893,195   5 Extended
/dev/sdb5          61,432,686   112,631,714    51,199,029   b W95 FAT32
/dev/sdb6         174,064,338   270,325,754    96,261,417   b W95 FAT32
/dev/sdb3         112,631,715   174,064,274    61,432,560   b W95 FAT32

/dev/sdb2 overlaps with /dev/sdb3

blkid -c /dev/null: ____________________________________________________________

sda1: LABEL="W1" UUID="282B-F7AE" TYPE="vfat" 
sda5: LABEL="W2" UUID="383D-BD2A" TYPE="vfat" 
sda6: UUID="DC2865F42865CDD8" LABEL="W3" TYPE="ntfs" 
sda7: UUID="DAEC8011EC7FE663" LABEL="W4" TYPE="ntfs" 
sda8: LABEL="W5" UUID="4E5C-C41B" TYPE="vfat" 
sda9: UUID="1c20fb1e-84da-4503-9815-9d5981a0cd6e" TYPE="ext4" 
sda10: UUID="f4b12394-3d5a-45b8-be3b-cf547c2e492f" TYPE="swap" 
sdb1: LABEL="WDC1" UUID="7C95-1978" TYPE="vfat" 
sdb5: LABEL="WDC2" UUID="5141-E757" TYPE="vfat" 
sdb6: LABEL="WDC4" UUID="50E6-B14E" TYPE="vfat" 
sdb3: LABEL="WDC3" UUID="508C-CCA4" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda9 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jorge/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jorge)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=jorge)
/dev/sda8 on /media/W5 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda7 on /media/W4 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/W1 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda5 on /media/W2 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6 on /media/W3 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb6 on /media/WDC4 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb3 on /media/WDC3 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb1 on /media/WDC1 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\ = "Sistema operativo no identificado en la unidad C."


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\ = "Sistema operativo no identificado en la unidad C."


=========================== sda9/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,9)
search --no-floppy --fs-uuid --set 1c20fb1e-84da-4503-9815-9d5981a0cd6e
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 1c20fb1e-84da-4503-9815-9d5981a0cd6e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1c20fb1e-84da-4503-9815-9d5981a0cd6e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,9)
	search --no-floppy --fs-uuid --set 1c20fb1e-84da-4503-9815-9d5981a0cd6e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1c20fb1e-84da-4503-9815-9d5981a0cd6e ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 282b-f7ae
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod fat
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 7c95-1978
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=1c20fb1e-84da-4503-9815-9d5981a0cd6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=f4b12394-3d5a-45b8-be3b-cf547c2e492f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda9: Location of files loaded by Grub: ===================


  73.7GB: boot/grub/core.img
  73.7GB: boot/grub/grub.cfg
  73.7GB: boot/initrd.img-2.6.31-14-generic
  73.7GB: boot/vmlinuz-2.6.31-14-generic
  73.7GB: initrd.img
  73.7GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


================================ sdb1/BOOT.INI: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```


As you said, it is rather longish. It does contain a lot of information, but I feel at a loss and don't know what to do with it. Perhaps you can help me. There are obviously some errors in the report of partitions, but not a hint how to correct them.
After writing the above, and upon rereading the Results in the Preview Post, I'm not so sure that Ubuntu is not within my 2nd drive, the 80 GB one. I got to reread it under windows and try to find the reported size, that should then be less than the 80 GB. If so my initial purposes have been defeated.

---

### Post by meierfra. on 2010-01-01
> Disco /dev/sda: 80.0 GB,

> sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

Ubuntu is on the partition /dev/sda8. So Ubuntu is on the 80GB drive /dev/sda.


> /dev/sdb2 overlaps with /dev/sdb3

The partition table of /dev/sdb is messed up. To fix it, boot into a Ubuntu and download the attach file PT.txt to your desktop. Rewrite the partition table with
```

cd ~/Desktop
sudo sfdisk --no-reread -f /dev/sdb -O PT.save < PT.txt
```
For emergency purposes, save the file PT.save somewhere outside your hard drives (flash drive, online storage,...)

Reboot. Gparted should now be able to see the partitions on your 160 GB drive /dev/sdb.

---

### Post by Coco999 on 2010-01-02
SUCCESS!!!

Thank you, meierfra, for your advice, that did the trick, definitely smarter than having to reformat all of the HD.
I corrected the partition table, then gparted could see the partitions and I installed UBUNTU 9.10 into the unallocated space (21 GB)I had allowed on purpose in my 160 GB disk. Just to be sure I had disconnected the 2nd drive, an 80 GB disk.

I wonder how you did to establish the right settings for the corrected partition table. I'll study the available info to try to figure out. 

A little detail, or quiz I would say, is that I can't invoke GParted from the installed Ubuntu, I can't find it. In the live  CD mode, it is readily available. To clarify things I installed in Spanish, while in the live I used English, but the language should not alter anything.

I'll leave the thread open for a couple of days, just in case, and then close it as solved.

Thank you to everybody who helped me.

---

### Post by QrK0 on 2010-01-03
> **Coco999 said:**
> SUCCESS!!!

A little detail, or quiz I would say, is that I can't invoke GParted from the installed Ubuntu, I can't find it. In the live  CD mode, it is readily available. To clarify things I installed in Spanish, while in the live I used English, but the language should not alter anything.


I think Gparted is not installed by default. Anyway, you can know if it is installed by running:

```
$ dpkg -l | grep gparted
```

If it is not installed, a simple

```
$ sudo apt-get install gparted
```

will do the work.

---

