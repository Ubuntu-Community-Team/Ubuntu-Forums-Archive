---
title: "root file system not detected?"
date: 2011-08-11
forum: General Help
---

### Post by nkrebs on 2011-08-11
i installed wubi and and during the verification stage, an error message saying that the root file system was not detected. i have no idea what to do as i am completely new to wubi and ubuntu. every other forum that has this problem confuses me because i don't know what it means. ( :( ) can you help me?

---

### Post by Rubi1200 on 2011-08-12
Hi and welcome to the forums :-)

There are a number of possible causes for this error, so you need to answer the following questions please.

1. is/was the disk part of a RAID array?

2. are the disks labeled as Dynamic in the Windows Disk Management utility?

3. do/did you have a GPT layout on the disks?

Thanks.

---

### Post by nkrebs on 2011-08-12
1. yes

2. i dont think so, but i don't know where it would say they would be.

3. a what?

---

### Post by Rubi1200 on 2011-08-13
You need to tell us what kind of RAID setup you have.

Wubi installs to RAID are not supported, but they are, in theory, possible.

If you can, post the results of the boot info script. There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by nkrebs on 2011-08-13
well i don't know how to tell (again), but i think i have a raid-0. i only have one hard drive but its partitioned 3 ways and it says there are 2 different hdd but there's only one inside. i will post the boot info script within 3 days as i am going away for the weekend but thank you for your help it is great!

---

### Post by Rubi1200 on 2011-08-13
Okay, I will keep an eye on the thread and respond once you have posted the results of the boot script.

Thanks.

---

### Post by nkrebs on 2011-08-15
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda5 starts at sector 1404594176.
    Operating System:  
    Boot files:        /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848 1,404,592,359 1,404,385,512   7 NTFS / exFAT / HPFS
/dev/sda3       1,404,594,174 1,928,880,127   524,285,954   5 Extended
/dev/sda5       1,404,594,176 1,928,878,079   524,283,904   7 NTFS / exFAT / HPFS
/dev/sda4       1,928,880,360 1,953,118,439    24,238,080   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              iso9660    Ubuntu 11.04 amd64
/dev/loop1                                              squashfs   
/dev/sda1        AE40B48640B45735                       ntfs       SYSTEM
/dev/sda2        FE22B55022B50EA1                       ntfs       Windows 7
/dev/sda4        FEE2B67BE2B6382B                       ntfs       FACTORY_IMAGE
/dev/sda5        38FC2E1FFC2DD7C0                       ntfs       Linux

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda5/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

umount: /isodevice: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(:cool: or fuser(1))
```

---

### Post by nkrebs on 2011-08-20
is that the right thing to post?

---

### Post by Rubi1200 on 2011-08-20
Sorry for the delayed response, busy at work.

Yes, this is the right information.

There seems to be a problem with mounting the Wubi install.

I suggest the following:

boot the computer with the LiveCD and run the following commands in the terminal:

```
sudo mkdir /media/win 
sudo mount /dev/sda5 /media/win 
sudo fsck /media/win/ubuntu/disks/root.disk
```After the last command has completed, run this to mount the root.disk:

```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```If you can access the root.disk, then you should be able to reboot, taking out the CD, and be back in Ubuntu.

Let me know how it goes please.

---

### Post by bcbc on 2011-08-20
Although I can't see any evidence of raid in the bootinfoscript, if you do have a raid0 setup this might apply: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/828330](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/828330)

---

