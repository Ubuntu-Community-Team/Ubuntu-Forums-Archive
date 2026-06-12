---
title: "error: no such partition"
date: 2011-10-27
forum: General Help
---

### Post by TheNavigator on 2011-10-27
I had this error after I made a new partition then I deleted it...

I went to find a solution, then I got Windows Vista to work, but I want to restore Ubuntu

I went to this tutorial. [http://ubuntuforums.org/showthread?t=1581099](http://ubuntuforums.org/showthread?t=1581099)

I got my Live Ubuntu USB drive, but I couldn't mount my ext2 partition. It said ```
you must specify the filesystem type
```

So I simply wrote ```
sudo mount ext2 /dev/sda2 (the ubuntu partition) /mnt/boot (as specified in tutorial)
```

Unfortunately,

```
[  963.531689] EXT2-fs (sda2): error: unable to read superblock
```

So, can someone help? :confused:

---

### Post by Rubi1200 on 2011-10-27
Hi and welcome to the forums :)

Please post the results of the boot info script so we can get a better idea of what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by TheNavigator on 2011-10-27
Here you are :)

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Lilo is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7369928 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 NTFS / exFAT / HPFS
/dev/sda2         163,848,190   488,375,999   324,527,810   f W95 Extended (LBA)
/dev/sda5         327,693,933   488,375,999   160,682,067   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 21 sectors/track, 4334 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192     7,827,455     7,819,264   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2420811A2080F3D8                       ntfs       
/dev/sda5        326AAA166AA9D6BF                       ntfs       
/dev/sdb1        40FB-197B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

/home/ubuntu/Downloads/boot_info_script060/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Rubi1200 on 2011-10-27
According to the script results sda2 is an extended partition and sda5 has no operating system on it. 

The Vista install appears to be okay.

I suppose the only thing I can suggest is reinstalling Ubuntu to sda5 but I may have missed something and you might want to wait for other opinions.

---

### Post by TheNavigator on 2011-10-27
Vista is installed on sda1

sda2 is where UBUNTU is installed

sda5 is completely another partition

I want to recover that Ubuntu version that was installed on sda2 :/

Will restoring windows to a backup point work?

---

### Post by Quackers on 2011-10-27
No it won't.
No operating system has been installed in your present sda2 partition. As it's an extended partition it only exists as a container for logical partitions eg sda5,sda6 etc, etc.
However a previous sda2 with a different partition type could have held an operating system - possibly.

You mention in post #1 that you "got Vista to work". What had happened and how did you get Vista to work? Did you run a recovery disc?

---

### Post by TheNavigator on 2011-10-27
I run that set root(hd0,0) thing

Now I reinstalled Ubuntu. It came to grub install and said fatal error grub-install /dev/sda6

What to do? :(

---

### Post by Rubi1200 on 2011-10-29
Please post the results of the boot info script again so we can see what has changed.

---

### Post by TheNavigator on 2011-10-30
Well, I just reinstalled it again and used the partition as ext 3 and it works :)

Thanks :)

---

