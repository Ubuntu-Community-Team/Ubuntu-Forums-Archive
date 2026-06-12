---
title: "Wubi refused to work even after chkdsk /r"
date: 2012-01-21
forum: General Help
---

### Post by GPilot on 2012-01-21
I'm having the same issue. I tried several times to reinstall wubi and rerun chkdsk /r but it didn't work...

---

### Post by Rubi1200 on 2012-01-21
Hi and welcome to the forums :-)

I have moved your post to its own thread.

Please start your own thread in future as no two problems are exactly alike and it dilutes community effort when trying to offer help.

Right now, I suggest you use the following guide to check if the root.disk is missing:
[COLOR=Black]Another recurring problem, missing the root.disk on a Wubi install, is dealt with here by forum member bcbc:
[http://ubuntu-with-wubi.blogspot.com...-rootdisk.html]("http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html")[/COLOR]

---

### Post by GPilot on 2012-01-22
Hi,

first of all, thanks for the quick response!
I looked for root.disk and found it, so I don't think the issue is there.
Here is what I get when selecting Ubuntu as boot option (I made a picture and later copied it from that picture):

[FONT=Courier New]Completing the Ubuntu installation.
For more installation boot options, press `ESC' now...
[it gives me a countdown from 3 to 0]
udevd[119]: inotify_add_watch(6, /dev/dm-4, 10) failed: No such file or directory


BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
mount: mounting /dev/dm-3 on /tmpmountpoint failed: No such device

Could not find the installation files /ubuntu/install/custom-installation
This could also happen if the file system is not clean because of an operating
system crash, an interrupted boot process, an improper shutdown, or unplugging,
of a removable device without first unmounting or ejecting it. To fix this, 
simply reboot into Windows, let it fully start, log in, run 'chkdsk /r', then
gracefully shut down and reboot back into Windows. After this you should be
able to reboot again and resume the installation.

_[/FONT]

Besides the last paragraph I don't understand much of the output...

---

### Post by Rubi1200 on 2012-01-22
You need to get hold of a LiveCD/USB and then post the output of the bot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by GPilot on 2012-01-23
This is my output:


                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/mapper/isw_cdjibdbich_ARRAY0.
 => Windows is installed in the MBR of /dev/mapper/isw_cdjibdbich_ARRAY1.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

isw_cdjibdbich_ARRAY01: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cdjibdbich_ARRAY02: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cdjibdbich_ARRAY03: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_cdjibdbich_ARRAY04: ________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_cdjibdbich_ARRAY11: ________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       240,974       240,912   6 FAT16
/dev/sda2             241,664    21,012,479    20,770,816   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,012,480 2,053,691,391 2,032,678,912   7 NTFS / exFAT / HPFS
/dev/sda4       2,053,691,902 2,313,960,959   260,269,058   f W95 Extended (LBA)
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.

/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               8,192     7,744,511     7,736,320   b W95 FAT32


Drive: isw_cdjibdbich_ARRAY0 _____________________________________________________________________

Disk /dev/mapper/isw_cdjibdbich_ARRAY0: 1932.7 GB, 1932735545344 bytes
255 heads, 63 sectors/track, 234975 cylinders, total 3774874112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_cdjibdbich_ARRAY01                 63       240,974       240,912   6 FAT16
/dev/mapper/isw_cdjibdbich_ARRAY02            241,664    21,012,479    20,770,816   7 NTFS / exFAT / HPFS
/dev/mapper/isw_cdjibdbich_ARRAY03   *     21,012,480 2,053,691,391 2,032,678,912   7 NTFS / exFAT / HPFS
/dev/mapper/isw_cdjibdbich_ARRAY04      2,053,691,902 2,313,960,959   260,269,058   f W95 Extended (LBA)
Empty Partition.


Drive: isw_cdjibdbich_ARRAY1 _____________________________________________________________________

Disk /dev/mapper/isw_cdjibdbich_ARRAY1: 67.7 GB, 67664871424 bytes
255 heads, 63 sectors/track, 8226 cylinders, total 132157952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_cdjibdbich_ARRAY11              2,048   132,155,391   132,153,344   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_cdjibdbich_ARRAY0p1 07DA-0919                              vfat       DellUtility
/dev/mapper/isw_cdjibdbich_ARRAY0p2 BE5E61685E611A83                       ntfs       RECOVERY
/dev/mapper/isw_cdjibdbich_ARRAY0p3 682AEB7A2AEB43A2                       ntfs       
/dev/mapper/isw_cdjibdbich_ARRAY1p1 F44287014286C7B6                       ntfs       DATAPART1
/dev/sda                                                isw_raid_member 
/dev/sdc1        3663-3763                              vfat       JORGOS-IMG

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_cdjibdbich_ARRAY0
isw_cdjibdbich_ARRAY0p1
isw_cdjibdbich_ARRAY0p2
isw_cdjibdbich_ARRAY0p3
isw_cdjibdbich_ARRAY1
isw_cdjibdbich_ARRAY1p1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4


Unknown BootLoader on isw_cdjibdbich_ARRAY01


Unknown BootLoader on isw_cdjibdbich_ARRAY02


Unknown BootLoader on isw_cdjibdbich_ARRAY03


Unknown BootLoader on isw_cdjibdbich_ARRAY04


Unknown BootLoader on isw_cdjibdbich_ARRAY11



========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf 

=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY01: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY01: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY02: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY02: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY03: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY03: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY04: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY04: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY11: No such file or directory
hexdump: /dev/mapper/isw_cdjibdbich_ARRAY11: No such file or directory
```

---

### Post by Rubi1200 on 2012-01-23
What kind of RAID do you have and where did you try installing Wubi?

Are you able to boot Windows normally?

---

### Post by imachavel on 2012-01-23
hmm, several partitions using raid

interesting concept, how does gparted see that? With one disk partitions must be contiguous. So what you would have is more then one partition on each disk, allocated as to what each partition could correctly write to, right??

---

### Post by GPilot on 2012-01-24
> **Rubi1200 said:**
> What kind of RAID do you have and where did you try installing Wubi?

Are you able to boot Windows normally?

Yes, Windows works perfect, I'm writing this in Windows. I selected the C: Partition for the Wubi installation. What is RAID? Is it a hard disk or partition? I'm a beginner at that kind of stuff.

---

### Post by GPilot on 2012-01-25
> **imachavel said:**
> hmm, several partitions using raid

interesting concept, how does gparted see that? With one disk partitions must be contiguous. So what you would have is more then one partition on each disk, allocated as to what each partition could correctly write to, right??
This is what I get when opening GParted in a Live session of Ubuntu.I posted the GParted window snapshot as attachment to this post.
 I just realized how unthoughtful it was of me not to tell you more  details on the several tries I already made with Linux. Before Wubi I  tried to install Ubuntu, Linux Mint and Fedora on the PC, normally with partitioning. But, as I dont have much experience in doing so I did probably most of the partitioning wrong. I probably  partitioned the wrong places with wrong formats. Because of that I never got it going, at the end it ended up in me recovering my  Windows 7 installation with the recovery CD. That was a year ago. Maybe there is a link between that wrong partitioning and the failed Wubi/installation... Again, sorry I didnt tell you  this before, I simply had forgotten that it might be of importance to  this subject.

---

### Post by GPilot on 2012-01-30
It have been 5 days. Anyone got any ideas? Maybe it's just me being inpatient, but has no one got an idea what the problem could be? Maybe someone knows in which direction I should start looking, because I honestly don't have an idea what this could be for a problem and how it could be fixed. Do you need some other special output? I would love to get into Linux, but as it seems this is kind of a big barrier between me and the free operating system.
Any responses are more than welcome,
GPilot

---

### Post by GPilot on 2012-02-03
Could someone please explain to me why there no one seems to have an idea? Don't want to be selfish, but I really would like to install it! And if it is not possible at least tell me so I don't have to check all the time if someone added something to the thread. RESPONSES, negative or positive, are more then welcome!!!:confused:

---

### Post by bcbc on 2012-02-03
This is an article on why RAID 10 doesn't work with Ubuntu (and how to get it to work): [http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/](http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/)

I would start by figuring out what sort of raid you have. Consult your manual or ask your supplier what the default setup came with your computer. That will help figure out how to resolve it.

---

### Post by GPilot on 2012-02-03
> **bcbc said:**
> This is an article on why RAID 10 doesn't work with Ubuntu (and how to get it to work): [http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/](http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/)

I would start by figuring out what sort of raid you have. Consult your manual or ask your supplier what the default setup came with your computer. That will help figure out how to resolve it.

First of all: Thank you for the quick response.
The article is on RAID 10, and the only detail I can find on my RAID  is that it is a SATA-RAID, I didn't find any info on RAID type/level. Is there any special command/program/method to find that out? I consulted the manual... it said just that. In the hardware management program it said SATA-RAID, too.

---

### Post by bcbc on 2012-02-03
There could also be some problems (not just a raid) which I think is likely:

> Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       240,974       240,912   6 FAT16
/dev/sda2             241,664    21,012,479    20,770,816   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,012,480 2,053,691,391 2,032,678,912   7 NTFS / exFAT / HPFS
/dev/sda4       2,053,691,902 2,313,960,959   260,269,058   f W95 Extended (LBA)
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.

/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Do you have a setting in BIOS that says what Raid you are using?

---

### Post by GPilot on 2012-02-04
In the BIOS menu the only thing it says is RAID: Array0 (or Array1 on the other hard drive).

---

### Post by bcbc on 2012-02-04
I don't use raid (so I'm not going to be much help) but a raid 0 should have 2 drives, and a raid 1 should have 2 drives.

I think you need to find someone with some expertise to help you figure out what's going on with your setup before you can solve the problem of installing Ubuntu. (Or just plug in another drive e.g. external; and install Ubuntu on that).

---

### Post by GPilot on 2012-02-05
> **bcbc said:**
> I don't use raid (so I'm not going to be much help) but a raid 0 should have 2 drives, and a raid 1 should have 2 drives.

I think you need to find someone with some expertise to help you figure out what's going on with your setup before you can solve the problem of installing Ubuntu. (Or just plug in another drive e.g. external; and install Ubuntu on that).

I will install it on an external hard drive! I didn't think of that option, but I think it's the best one for me. I don't want to mess around more with my PC at this point, as long as my Windows installation works perfectly I won't need any expertise... Thanks again for the idea. Is it OK if I mark this thread as solved?

---

### Post by bcbc on 2012-02-05
It's your thread, so it's up to you to decide whether it's solved. ;)

When you install to the external drive (assuming you do a direct install) make sure you install the grub2 bootloader to the external drive MBR, not your internal drive. (Otherwise when the external is not plugged in, it won't boot). Then whenever you want Ubuntu, you use the BIOS boot options key to override the bootorder to boot from the external (that's usually best).

PS check out this guide: [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html) It's written for release 10.10 but should be pretty much identical to whatever version you install. Pay particular attention to the part where you choose the "Device for bootloader installation". That will be your external drive. Since you already have /dev/sda,b,c it will be something like /dev/sdd (but you should confirm that).
Good luck.

---

### Post by GPilot on 2012-02-05
> **bcbc said:**
> It's your thread, so it's up to you to decide whether it's solved. ;)

When you install to the external drive (assuming you do a direct install) make sure you install the grub2 bootloader to the external drive MBR, not your internal drive. (Otherwise when the external is not plugged in, it won't boot). Then whenever you want Ubuntu, you use the BIOS boot options key to override the bootorder to boot from the external (that's usually best).

PS check out this guide: [http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html") It's written for release 10.10 but should be pretty much identical to whatever version you install. Pay particular attention to the part where you choose the "Device for bootloader installation". That will be your external drive. Since you already have /dev/sda,b,c it will be something like /dev/sdd (but you should confirm that).
Good luck.
I just followed the instructions and it worked! Finally! Thank you so much!:D

---

### Post by bcbc on 2012-02-05
> **GPilot said:**
> I just followed the instructions and it worked! Finally! Thank you so much!:D

Great to hear! You're very welcome.

---

