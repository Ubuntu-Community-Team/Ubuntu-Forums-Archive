---
title: "GRUB RESCUE Error"
date: 2011-11-21
forum: General Help
---

### Post by kernelgreen on 2011-11-21
After making some changes to my dual-boot XP + Ubuntu PC, I get the 
error message: 
error: no such device:UUID#

I have downloaded and run the boot script. The RESULTS Output is contained below. I'd appreciate some simple direction on how I may be able to edit my grub bootloading function to get my PC running again.

I'm a GUI kind of guy  :) -- the command line, while admirable, gives me 
anxiety. Therefore, GUI advise will be most helpful. 

Thanks for any advise!


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63    44,917,739    44,917,677   7 NTFS / exFAT / HPFS
/dev/sda2         167,798,925   204,668,099    36,869,175   7 NTFS / exFAT / HPFS
/dev/sda3         312,496,380   312,576,704        80,325  83 Linux
/dev/sda4          85,884,926   167,798,783    81,913,858   5 Extended
/dev/sda5    *     85,884,928   164,345,855    78,460,928  83 Linux
/dev/sda6         164,347,904   167,798,783     3,450,880  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        30001C24001BEF98                       ntfs       e3-XP-PROG
/dev/sda2        741887D718879730                       ntfs       e3DATA
/dev/sda5        dafcc17f-7e59-447d-880e-b3665c957120   ext4       UBU1010NB-6FEB11
/dev/sda6        b92f8b27-8b1d-49dc-95fc-7eb127d5b200   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=7
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

---

### Post by kernelgreen on 2011-11-21
While I was waiting for a reply I kept working. I was able to FIX this ISSUE by DOWNLOADING INSTALLING AND RUNNING a GUI
Program =  BOOT-REPAIR. 

[URL="https://help.ubuntu.com/community/Boot-Repair"]

https://help.ubuntu.com/community/Boot-Repair

I just ran the program and accepted the suggested changes. My eeePC NetBook booted right up when I rebooted -- XP and Ubuntu both available. Great Stuff!

---

