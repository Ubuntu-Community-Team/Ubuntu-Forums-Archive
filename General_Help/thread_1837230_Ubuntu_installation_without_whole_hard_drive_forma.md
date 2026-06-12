---
title: "Ubuntu installation without whole hard drive formatting"
date: 2011-09-01
forum: General Help
---

### Post by gexgik on 2011-09-01
Hi guys! I am a new commer in this great ubuntu world and  need some help. I decided to get rid of the old pirated windows 7 and to install ubuntu. I have created a bootable usb with ubuntu 11 and i am posting this from it right now. I have erased the windows 7 by formatting that partition. **The** **problem is that  i've decided to install ubuntu(now is running from usb) and it looks like when I am running the installer it is only the possibility of formatting whole hard drive.I've allready formatted the 116 gb partition where windows was installed. I don't want to format the hard disk. Can anyone help me to install definitely Ubuntu?! **Thank you and if I wasn't clear enough I will  give more details about my problem. (sorry for the english mistakes)

---

### Post by sanderd17 on 2011-09-01
You will probably need to go to the manual mode. Can you post the output of the boot info script? Follow the instuctions on this page: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by gexgik on 2011-09-01
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda3 has 
                       409597951 sectors, but according to the info from 
                       fdisk, it has 409600383 sectors.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       614399999 sectors, but according to the info from 
                       fdisk, it has 614402847 sectors.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 520 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
224 heads, 19 sectors/track, 293764 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       208,543       206,496   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   226,265,983   226,059,136   7 NTFS / exFAT / HPFS
/dev/sda3         226,263,040   635,863,423   409,600,384   7 NTFS / exFAT / HPFS
/dev/sda4         635,860,992 1,250,263,839   614,402,848   7 NTFS / exFAT / HPFS

/dev/sda1 overlaps with /dev/sda2
/dev/sda2 overlaps with /dev/sda3
/dev/sda3 overlaps with /dev/sda4
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1006 MB, 1006632960 bytes
65 heads, 32 sectors/track, 945 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     1,966,079     1,966,048   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6c91c171-53a4-464b-a91c-5a7db88f6787   ext4       linux2
/dev/sda2        6ffc4b62-f964-4bfc-972c-805bf39ee8f3   ext4       linux
/dev/sda3        EC28E77528E73CE8                       ntfs       WorkSpace
/dev/sda4        FAA8E4C1A8E47D8F                       ntfs       FunSpace
/dev/sdb1        1076-05BD                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/linux2            ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda2        /media/linux             ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/WorkSpace         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /media/FunSpace          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

** I want to keep the partitions created in Windows .**

---

### Post by sanderd17 on 2011-09-01
I don't know what you did, but this seems pretty bad. How did you erase your windows?

Partitions should not overlap each other.

> **gexgik said:**
> ```
 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
224 heads, 19 sectors/track, 293764 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       208,543       206,496   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   226,265,983   226,059,136   7 NTFS / exFAT / HPFS
/dev/sda3         226,263,040   635,863,423   409,600,384   7 NTFS / exFAT / HPFS
/dev/sda4         635,860,992 1,250,263,839   614,402,848   7 NTFS / exFAT / HPFS

/dev/sda1 overlaps with /dev/sda2
/dev/sda2 overlaps with /dev/sda3
/dev/sda3 overlaps with /dev/sda4
/dev/sda4 ends after the last sector of /dev/sda

```

---

### Post by gexgik on 2011-09-01
by formatting it's partition with Disk Utility

---

### Post by sanderd17 on 2011-09-01
Well, something went wrong.

Are you still able to access the files on the non-erased partitions? In that case, make sure you have a backup, because the chances are high that you are going to lose everything while trying to repair it.

Now, Disk utility is incapable of creating an ext4 partition, so sda1 and sda2 are certainly wrong. Normally, when you erased it, it should say that they are "unallocated".

I would suggest to start gparted (it's in one of the menus, depends on what interface you are using) and try to resize partitions and apply changes until you don't see those messages of "X overlaps with Y".

---

### Post by gexgik on 2011-09-01
:D I can access the files. gparted says to me that the 596 gb are unallocated. so it isn't any method to format that free space and install ubuntu on it?

---

### Post by sanderd17 on 2011-09-01
you can format the whole disk, but in the previous process with the Disk Utility, something went wrong and Ubuntu is in any case not able to solve it.

Are you still able to access the files on those partitions?

---

### Post by gexgik on 2011-09-01
yes

---

### Post by sanderd17 on 2011-09-01
Well, backup those.

And I found a tool that will probably be useful: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Install it from the **software center**, and try what you can do with it. I have never needed to repair broken partitions, so I don't know how it works to be honest.

---

### Post by gexgik on 2011-09-01
thank you so much for trying to help me. I'll try it right now and post here.

---

### Post by gexgik on 2011-09-01
i've downloaded the archive with the software in it but i can't open it with the software center. is there another method?

---

### Post by sanderd17 on 2011-09-01
you should open the software center and search for that app inside the software center. 

That's one of the beautiful things of Linux: certralised app management. There is no need to google an exe or so.

And once it is installed, it automatically gets updated with all other software (in an installed version off course, not in a live environment).

---

### Post by gexgik on 2011-09-01
i love this feature but I can't find that software in the software center.

---

### Post by sanderd17 on 2011-09-01
Ah, ok. I checked it here: [http://packages.ubuntu.com/natty/testdisk](http://packages.ubuntu.com/natty/testdisk)

But I didn't notice that it was in the Universe repositories. Those are not enabled by default (because they cause patent issues in certain countries like the USA or Japan). You have first to go to the "software sources" and enable the universe repository.

Sorry that I didn't notice it.

---

### Post by gexgik on 2011-09-01
thank you. another dumb  question, where I find the app after I've installed it? :D

---

### Post by sanderd17 on 2011-09-01
testdisk is probably no GUI tool (as I said, I never used it). So open a terminal (CTRL+ALT+T) and execute
```

[s]testdrive[/s] testdisk

```

Gui tools appear in the menus.
[B]
EDIT:[/B]

Sorry, it should be
```

sudo [s]testdrive[/s] testdisk

```

the sudo stands for "superuser do". Which gives more rights to the testdrive program. Normal programs only have the right to edit files owned by the user who is working with it (so they can't harm the OS installation). But programs executed as superuser (aka root) have rights to edit the entire hard disk (which is what you need here).

---

### Post by gexgik on 2011-09-01
sudo testdrive doesn't work. it may be "sudo testdisk" ?

---

### Post by sanderd17 on 2011-09-01
yes, it's testdisk, and not testdrive. Dont know why I said that, maybe have too much cars in my head :P

---

### Post by gexgik on 2011-09-01
:)) 
help me please to interpret this data..
```

Partition                  Start        End    Size in sectors

 1 * Linux                    0  32 33    12 250 14     206496 [linux2]
 2 P HPFS - NTFS          14084  56 53 39580 131 39  409597952 [WorkSpace]
 3 P HPFS - NTFS          39580 131 40 77825  37 36  614400000 [FunSpace]
```
the partition where windows was installed doesn't appear here, it is called linux and has about 100 gb...

---

### Post by sanderd17 on 2011-09-01
I start to understand.

If you look at the partition sizes of that boot info script, you see that the partition sda1 (with the label "linux") is very small compared to all others. 

So the disk utility probably created that small partition and a second partition with the label "linux2" (maybe this label was chosen automatically) is the original Windows installation.

I think the first partition doesn't really exists and causes your partitions to be shifted a few blocks, which in turn causes overlapping partitions.

So testdisk will be right that there is no partition with the label "linux", but the partition with the label "linux2" is your partition where Windows used to be.

BTW, you should post such things between CODE tags.

---

### Post by gexgik on 2011-09-01
after a deeper scan this is the result : 
```

Disk /dev/sda - 640 GB / 596 GiB - CHS 77825 255 63
     Partition               Start        End    Size in sectors
D Linux                    0  32 33    12 250 14     206496 [linux2]
D Linux                   12 223 20 14084 103 35  226059136 [linux]
D HPFS - NTFS          14084  56 53 39580 131 39  409597952 [WorkSpace]
* HPFS - NTFS          39580 131 40 77825  37 36  614400000 [FunSpace]

```linux and linux2 are the names I gaved them. 
thank you for trying to help me

**The question is : how can I format that linux partition so I can install ubuntu on that partition and leave the others untouched ?**

---

### Post by oldfred on 2011-09-01
Standard Windows 7 installs create a 100MB boot/recovery hidden partition to boot from and the main install or c: drive.

You can just delete the 100MB now linux2 partition as it is small and not very useful. It also is taking up one of the primary partitions which you may want back. You can only have 4 primary partitions, one of which can be an extended partition that can hold any number of logical partitions. Ubuntu works just fine from logical partitions but Windows has to boot from a primary partition.

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by gexgik on 2011-09-01
in gparted all my hard space appears as **unallocated** !!!

---

### Post by oldfred on 2011-09-01
Post each of these:

sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print
sudo sfdisk -l -uS

And backup current partition table with this

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by gexgik on 2011-09-02
```
sudo fdisk -lu /dev/sda
Disk /dev/sda: 640.1 GB, 640135028736 bytes
224 heads, 19 sectors/track, 293764 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ffe896b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      208543      103248    7  HPFS/NTFS
/dev/sda2          206848   226265983   113029568    7  HPFS/NTFS
/dev/sda3       226263040   635863423   204800192    7  HPFS/NTFS
/dev/sda4       635860992  1250263839   307201424    7  HPFS/NTFS
```
```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Error: Can't have overlapping partitions.  
```
```
ubuntu@ubuntu:~$ sudo sfdisk -l -uS

Disk /dev/sda: 77825 cylinders, 255 heads, 63 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/224/19 (instead of 77825/255/63).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048    208543     206496   7  HPFS/NTFS
/dev/sda2        206848 226265983  226059136   7  HPFS/NTFS
/dev/sda3     226263040 635863423  409600384   7  HPFS/NTFS
		start: (c,h,s) expected (1023,223,19) found (1023,69,2)
/dev/sda4     635860992 1250263839  614402848   7  HPFS/NTFS
		start: (c,h,s) expected (1023,223,19) found (1023,96,1)

Disk /dev/sdb: 1022 cylinders, 31 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/65/32 (instead of 1022/31/62).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        32   1966079    1966048   6  FAT16
		end: (c,h,s) expected (945,14,32) found (960,64,32)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

```

---

### Post by oldfred on 2011-09-02
I think sanderd17 was correct on partitions being shifted as everyone starts before the end of the previous and the last one ends after the end of the drive. See the fdisk output by sector.

Fixing overlapping is not straight forward as you can not be sure which partition the overlapping part really belongs to and if incorrect then you may corrupt data.

---

### Post by sanderd17 on 2011-09-02
> **oldfred said:**
> I think sanderd17 was correct on partitions being shifted as everyone starts before the end of the previous and the last one ends after the end of the drive. See the fdisk output by sector.

Fixing overlapping is not straight forward as you can not be sure which partition the overlapping part really belongs to and if incorrect then you may corrupt data.

I might be right about what the problem is, but I have absolutely no clue on how to solve it. If you know something, just say it, the only thing I can do now is using Google.

---

### Post by oldfred on 2011-09-02
I know of a way but I am not confident of all the calculations to make it work. You can use sfdisk to read the pt.txt file back in after editing a copy of it. But you have to have start and size info exactly correct as it then is your new partition table. All the outputs are starts & ends so you have to recalculate all the sizes.

Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by gexgik on 2011-09-03
So, anybody has any idea of how I can keep those 2 partitions and install UBUNTU on the free space?

---

### Post by oldfred on 2011-09-03
Until you get overlapping and last partition beyond end of disk issues resolved you will not be able to do anything.

What partitions have data, do you have good backups?

Post the PTsda.txt file that you backed up partiiton table to:

---

### Post by linuxuser12345 on 2011-09-03
The easiest way is just to back up all your files, install Ubuntu with format, and add your files back to your installation.

---

