---
title: "&quot;error loading operating system&quot;  partition problem"
date: 2010-09-18
forum: General Help
---

### Post by Shmits on 2010-09-18
Hello ubuntu forums! It's been quite a while seince I've been on, let me explain my situation. I have a 200 gig hard drive which I dual boot windows xp along with ubuntu 10.04, I used my windows partition for gaming, and bearly used ubuntu. I needed the hard drive space so I loaded my xp install cd to delete the Linux partitions on my drive and left my windows partition alone. After I deleted them I restarted to find the "error loading operating system" message after my bios screen. I did use a different bootloader than grub, I used burg which is a graphical bootloader I installed through Linux, I've tried to run the commands bootcfg /rebuild, fixboot and fixmbr in the recovery console from the xp cd to fix my problem with no luck. Can any one shed some light? Thanks!

---

### Post by Shmits on 2010-09-21
come on now people! :neutral:  can anyone help? or can you tell me where else to search for answers?

---

### Post by Rubi1200 on 2010-09-21
Did you run the commands exactly as outlined here?
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Do you have an Ubuntu CD?

If yes, boot the computer choosing to try in live mode and post the results of the bootscript linked to at the bottom of my post.

---

### Post by Shmits on 2010-09-23
thank you, here are the results:








 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
228 heads, 21 sectors/track, 130564 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   359,822,126   359,822,064   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 252 MB, 252968960 bytes
16 heads, 32 sectors/track, 965 cylinders, total 494080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 101       494,079       493,979   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FEC45348C4530277                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3131-6435                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/3131-6435         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows G4MING Edition" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows G4MER Edition" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="" 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"

---

### Post by gypsumwolf on 2010-09-23
**See what these other guys say first, but** when I get the No Operating System found (without seeing Grub screen) or if I end up getting a bunch of 1s and/or 0s on the screen, I boot a live cd, and if it is a ubuntu live cd I do this: [**WARNING WILL ERASE EVERYTHING** (As far as most people's view of it)]

```
apt-get install wipe
wipe /dev/sda
```

I only run it for a minute or less, because it wipes the MBR (I assume) and then I can reinstall everything just fine and it will boot just fine to. Although Everything you had on the drive will (as far as most people are concerned) be **ERASED FOREVER!**

Note: some Linux distros like GRML (An awesome distro) may come with wipe on the CD so you dont have to install it first.

---

### Post by Shmits on 2010-09-24
Your telling me i have to completely wipe my drive to fix this? I have over 20 games installed on that windows partition? You sure there's no other way? Thanks guys for the help this far, buy the way!

---

### Post by Quackers on 2010-09-24
Not at this stage.
When you run the xp cd and go into the recovery environment and used the fixboot and fixmbr commands, what happened? What came up on the screen? Was the xp installation found?

---

### Post by Mark Phelps on 2010-09-24
> **Shmits said:**
> ...I've tried to run the commands bootcfg /rebuild, fixboot and fixmbr in the recovery console from the xp cd to fix my problem with no luck.

What you've told folks is that you've already done the usual repair stuff -- and nothing has worked.

There is no such thing as XP Gamer edition, at least, NOT from MS. If this was some hacked version you downloaded from a Warez site, since those often omit stuff, and patch other stuff to avoid activation problems, you could have a very hard time getting it working again. 

I notice that you have four OS entries in your boot.ini file. You could try removing all but the last entry and see if that works.

There have been some threads in the Installation forum on how to replace an MS Windows MBR using Lilo from a Linux CD.  Suggest you go to that forum and do a search.

And finally, as to your complaining about lack of answers ... these are the "Ubuntu forums", not the "Windows XP" forums.  While many folks here use XP, we don't hold ourselves out to be the experts in repairing XP problems.

---

### Post by gypsumwolf on 2010-09-26
> **Shmits said:**
> Your telling me i have to completely wipe my drive to fix this? I have over 20 games installed on that windows partition? You sure there's no other way? Thanks guys for the help this far, buy the way!

You can boot your computer with a Linux LiveCD and access your hard drive, copy all the files you want onto a external hard drive, DVD or CD(s). Than you can use wipe on your hard drive for like 1 minute then stop the program from running (Ctrl+C). Then you can reinstall windows and everything you backed up. It is not a hard task to accomplish, it just takes some time (maybe 2-3 hours to get your system completely back to how you want it).

---

