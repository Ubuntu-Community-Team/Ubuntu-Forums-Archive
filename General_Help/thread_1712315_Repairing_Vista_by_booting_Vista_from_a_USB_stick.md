---
title: "Repairing Vista by booting Vista from a USB stick"
date: 2011-03-22
forum: General Help
---

### Post by dragonfly41 on 2011-03-22
I am trying to boot up Vista Home Premium from USB since my internal (bootable) CD-RW drive has failed and I cannot boot up Vista from CD.

I have Ubuntu running in the Windows partition and all my windows files are in there so I don't want to do a full installation of Ubuntu (yet).

I formatted an 8GB USB stick into two partitions

/dev/sdb1    Fat32   /media/Vista     Vista      3.71 GB       flag boot
/dev/sdb2    Fat32   /media/Other    Other    3.76 GB

I then copied over to    /dev/sdb1   all files from a Vista CD using an external CD-RW drive (which is not recognised as bootable on USB port).

In my Dell BIOS settings  I changed the boot sequence to be bootable from USB disk first.

then I tried to reboot Vista installation in the USB stick.

But I get this message ...

"this is not a bootable disk .. insert a bootable floppy"

So I could not boot up the Vista installation files.

When the boot flag is "on" in a GParted created partition does this make the partition DOS bootable for Vista installation?   

My question is - What utility in Ubuntu 10.10 can create a DOS bootable partition on a USB stick?   It seems that the MBR might have been overwritten when I installed Grub 2.0.

I can Grub dual boot between Windows and Ubuntu but I can't get very far with Windows .. stalls in safe mode.

So a Vista repair is called for.   I would prefer not to reinstall Vista afresh at this stage.

There is a thread here explaining how to repair Vista bootloader

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

but it assumes that I am able to boot from CD-RW drive.

---

### Post by Mark Phelps on 2011-03-22
> **dragonfly41 said:**
> My question is - What utility in Ubuntu 10.10 can create a DOS bootable partition on a USB stick?
Not aware of any.  Unetbootin, which is what MOST folks will recommend, only allows you to make Linux boot USBs.

Suggest you go to a Windows 7 forum (sevenforums.com) and look through the tutorials they have about Installation.  I believe there is one about creating a Win7 bootable USB installer -- and the steps would be essentially the same for Vista.

---

### Post by dragonfly41 on 2011-03-22
I tried this tutorial which suggests using freedos

[http://www.aselabs.com/articles.php?id=243](http://www.aselabs.com/articles.php?id=243)

[COLOR=DarkRed]The only software that you will need to install is the package called "dosemu" which is very simple to install from Synaptic or the console.[/COLOR]

but I don't have much success in installing *any* packages ... 

[COLOR=Blue]ubuntu@ubuntu:~$ sudo apt-get install dosemu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dosemu
ubuntu@ubuntu:~$ [/COLOR]

Is this because I'm using ubunto in demo mode?

...

freedos is also used here ..

[http://www.justlinux.com/forum/showthread.php?t=148499](http://www.justlinux.com/forum/showthread.php?t=148499)

but how to install it?

---

### Post by wilee-nilee on 2011-03-22
With W7 I have gotten this to work every time.

Format the usb with a ntfs partition in gparted put a bootflag on that partition, then use the file roller to extract the vista to the partition.

---

### Post by ppv on 2011-03-22
You may probably  need another system running windows as only creating a bootable partition may not do it....try googling bartpe...that is the boot environment for setting up USB disk windows.

---

### Post by dragonfly41 on 2011-03-22
I followed advice of wilee-nilee and I got as far as booting up from USB and it seemed that windows started installing.

Large cursor on screen which could be moved (not frozen) and some activity in disk lights.   

But after a long time it just stuck in black screen .. cursor could be moved around .. but no sign of further installation.   Don't know how long to wait.

I'll have to try copying the Vista files again from CD into USB.

I've used the boot info script and here are the results showing that Windows is in the /dev/sda

/dev/sdb is the 8 GB USB stick in two partitions

/dev/sdb1 contains Vista (bootable flag set)
/dev/sdb2 contains miscelaneous files.


                [COLOR=Blue]Boot Info Script 0.55    dated February 15th, 2010                    

============================= 
Boot Info Summary: 
==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2:
 _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 7784448.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== 
Drive/Partition Info: 
=============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       401,624       401,562  de Dell Utility
/dev/sda2             403,456    21,374,975    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,374,976   483,151,863   461,776,888   7 HPFS/NTFS
/dev/sda4         483,151,872   488,394,751     5,242,880   f W95 Ext d (LBA)
/dev/sda5         483,153,920   488,394,751     5,240,832  dd Dell Media Direct


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8019 MB, 8019509248 bytes
247 heads, 62 sectors/track, 1022 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048     7,784,447     7,782,400   7 HPFS/NTFS
/dev/sdb2           7,784,448    15,663,103     7,878,656   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              iso9660    Ubuntu 10.10 i386             
/dev/loop1                                              squashfs                                 
/dev/loop2       48596993-88ee-4a4f-a2b7-d5b79073ccde   ext4                                     
/dev/sda1        07D8-0508                              vfat       DellUtility                   
/dev/sda2        5204ADEB04ADD271                       ntfs       RECOVERY                      
/dev/sda3        C8A6B0E3A6B0D364                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        72B4-788D                              vfat       MEDIADIRECT                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5A0D18B62CA3DE07                       ntfs       Vista                         
/dev/sdb2        018A-2665                              vfat       Other                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0E686A82686A6883                       ntfs       FreeAgent Drive               
/dev/sdc: PTTYPE="dos" 

============================ 
"mount | grep ^/dev  output: 
===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/Other             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb1        /media/Vista             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/FreeAgent Drive   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ 
sda5/boot.ini: 
================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024 

=============================== 
StdErr Messages: 
===============================

umount: /isodevice: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))[/COLOR]

---

### Post by dragonfly41 on 2011-03-23
I have a supplementary question ..

Since I have an external CD-RW drive on USB port  which can load Vista installation disk .. currently reloading files into USB stick

Instead of booting up Vista installation disk copied into bootable USB stick would it be feasible to place a "proxy" DOS batch file in bootable USB stick (instead of all the Vista installation files) to run the setup.exe in the external CD installation disk?   Or is this a daft idea?

---

