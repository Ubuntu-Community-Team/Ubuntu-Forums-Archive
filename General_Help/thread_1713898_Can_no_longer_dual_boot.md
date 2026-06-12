---
title: "Can no longer dual boot"
date: 2011-03-24
forum: General Help
---

### Post by acidblue on 2011-03-24
I had to reinstall Win Xp on my dual boot system.
After reinstall I could boot into Ubuntu but not XP, unless I had the XP
install disk in the cd drive.

I followed this to reinstall grub2: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I do have *grub.cfg* But I still cannot boot into XP even though it is
listed in the boot menu when I reboot my PC.
Any ideas on what i should try?

Ubuntu 10.04 64bit

---

### Post by wilee-nilee on 2011-03-24
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Have you run any chkdsk on the XP?

Have you run a update grub in Ubuntu?

---

### Post by acidblue on 2011-03-24
> **wilee-nilee said:**
> So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Have you run any chkdsk on the XP?

Have you run a update grub in Ubuntu?


No i haven't done chkdsk nor update grub.

Results of boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 117706144 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   299,808,767   299,806,720  83 Linux
/dev/sdb2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sdb5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        74AC53B7AC53731A                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        bb33ea81-6753-405a-8d14-b749684dac91   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        363fb3d8-c164-4e95-9ef5-c0ef84c2614b   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="winxp" n

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="winxp" 

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


=========================== sdb1/boot/grub/grub.cfg: ===========================

```

---

### Post by wilee-nilee on 2011-03-24
Put all the bootscript text in that last post.

---

### Post by acidblue on 2011-03-24
After doing a *bootcfg /rebuild* in Windows and a *grub-update *
I am now able to boot into Win XP.

---

