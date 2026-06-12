---
title: "No GRUB after dual-booting Ubuntu and Windows 7 on HP"
date: 2012-01-17
forum: General Help
---

### Post by kingmetalx on 2012-01-17
Hello :)

I've tried doing this over and over the last few weeks, but every time I end up using the HP Recovery Tools to reformat my entire computer.

Anyway, the problem is that after I install Ubuntu 11.10 (and even 11.04) alongside Windows 7 on my HP Pavillion, my computer does one of two things:  it will automatically boot to Windows 7 with no GRUB or it will tell me that there is no GRUB and it won't let me boot to either partition.  What is happening right now is the former - it goes directly to Windows 7.  On past tries, it took a few reboots and shutdowns before anything weird happened, but it would always mess up in the end.

Any suggestions?  Thanks!

---

### Post by mattdlyons00 on 2012-01-17
In which order did you install each operating system

---

### Post by kingmetalx on 2012-01-17
Windows 7, then Ubuntu 11.10.

Here is my Boot Info Script:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

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
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>........D.8...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 7379656 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   757,259,266   757,052,419   7 NTFS / exFAT / HPFS
/dev/sda3         952,932,352   976,771,071    23,838,720   7 NTFS / exFAT / HPFS
/dev/sda4         757,260,286   952,932,351   195,672,066   5 Extended
/dev/sda5         757,260,288   947,480,575   190,220,288  83 Linux
/dev/sda6         947,482,624   952,932,351     5,449,728  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,856,126     7,856,064   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        BA2405EE2405AF07                       ntfs       SYSTEM
/dev/sda2        3E76074B7607037F                       ntfs       OS
/dev/sda3        4C28006328004F00                       ntfs       HP_RECOVERY
/dev/sda5        17b89c52-2857-45e1-b732-ecac1713e0ce   ext4       
/dev/sda6        b61c1bf3-4417-4f84-ab17-e7b37e29361f   swap       
/dev/sdb1        9A27-1844                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================
```

---

### Post by carl4926 on 2012-01-17
Are you writing grub to the MBR of sda

---

### Post by kingmetalx on 2012-01-17
I'm not very knowledgeable in that area.  The only thing that I ever do when installing Ubuntu is follow the setup screens.  The only thing that I had done when all of this happened was choose "Install Ubuntu alongside...," then finished setup and installation, it told me to restart, and then it went straight to Windows 7 without showing GRUB.

And sdb1 is my pendrive.

---

### Post by carl4926 on 2012-01-17
By default the installer 'should' choose to do as I describe

I have never used the "Install Ubuntu alongside...,"
I always go 'Custom for Advanced users'
And manually allocate the partitions.
You should see the bootloader options, I think it's just after entering your user and password info..

Let me check...

---

### Post by kingmetalx on 2012-01-18
Any more suggestions?

---

### Post by carl4926 on 2012-01-18
> **kingmetalx said:**
> Any more suggestions?

So what are you doing at this part
[http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg](http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg)

see also
[http://dl.dropbox.com/u/10573557/Ubuntu/ub_11.10_slideshow.mkv](http://dl.dropbox.com/u/10573557/Ubuntu/ub_11.10_slideshow.mkv)

---

### Post by syerges on 2012-01-18
I hope this helps:
[http://superuser.com/questions/314241/dual-boot-install-no-grub](http://superuser.com/questions/314241/dual-boot-install-no-grub)

---

### Post by marcellux on 2012-01-18
hi, 

is that a HP Pavilion dvX-XXXX?

It comes with WIndows 7 already installed and some extra funny partitions for HP tools, recoveries, and some other stuff.

I did not try to install Ubuntu alongside, but I did do use the windows shrink tool to create a new partition to install Linux. The results were, I could not boot Linux either, no Grub to be found.

So, I formatted the entire HDD, I created 3 partitions, one for Windows, one for Linux and one for Data. I first installed Windows 7, (it creates itself an extra filesystem partition around 100  MB large), and finally Linux. GRUB took over, I could choose what OS to start.

(btw I am using KUBUNTU 11.10)

---

### Post by oldfred on 2012-01-18
You should not have to reinstall just to fix the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

You can use this tool to repair also.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Or perhaps this one.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

There was some HP software that interfered with grub and after booting into Windows it would write into the sectors after the MBR where grub has some code.
In Windows 7, had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)

Some other issues, quotes from others:
> I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. 
Thus it seems the my antivirus scans the master boot record and as it finds something strange (Grub), it kind of deletes it and make my Boot bugged.
I un-installed norton and a gateway recovery management application and that seems to have fixed it.


---

### Post by Andrewpaul on 2012-02-21
Hi,
First, download EasyBcd (open souce software developed by Ubuntu).
 
Link; [Download EasyBCD 2.0.2.117 Free - A handy tool for tweaking your system - Softpedia]("http://www.softpedia.com/get/System/OS-Enhancements/EasyBCD.shtml")
 
Install it with Windows 7, and run the EasyBcd. 
 
Note: Don't delete the original entry of Windows 7 in EasyBcd.
 
You just need to add another entry for your Ubuntu. (Those settings with  check box in EasyBcd under the last menu bar, just ignore it. By the  way, you can change the name of the Windows 7 entry in EasyBcd (remove  entry and rename entry are two different things)). Just to get the issue  solve, you don't rename it first, because you may do something worst  later as you confuse. Rename after you settle down the issue.
 
Restart, you are done, everything will work as fine as you wish.

[http://www.techyv.com/questions/windows-7-boot-error-after-installing-dual-os-ubuntu](http://www.techyv.com/questions/windows-7-boot-error-after-installing-dual-os-ubuntu)

---

