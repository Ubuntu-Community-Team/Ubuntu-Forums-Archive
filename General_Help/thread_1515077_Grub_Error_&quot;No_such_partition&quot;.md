---
title: "Grub Error: &quot;No such partition&quot;"
date: 2010-06-21
forum: General Help
---

### Post by aaroncam2 on 2010-06-21
Ok, so I have 10.04 Netbook installed on my EEE pc. I dual boot windows and linux choosing between them through the menu grub provides. But I when I booted up today I selected windows recovery console instead of windows xp by accident, and the recovery process started automatically without me doing anything! so anyway i thought everything would be fine and i would just end up with windows xp recovered and ubuntu untouched, but instead when I boot up i get the error,

error: no such partition
grub rescue>

before i can even select my os. Please help, thanks.

---

### Post by Alan Jack on 2010-06-21
Did exactly the same.

As best I can tell, its wiped the partition header for the linux partition, and I can't get anything to recover it.

GParted (running off the USB drive) is showing a 27 gig partition (which is mounted, and I've looked at, and it's Windows) and a 4.89 gig partition (which was hidden, I've un-hidden it, and its the recovery partition).  But between these is 117 gigs of an "unknown" partition.

I reinstall from factory default, but I'm on holiday and all my photos are in the unknown partition!!!

Help!

Have tried installing/running TestDisk, but it didn't seem to find anything.

---

### Post by wilee-nilee on 2010-06-22
Post the bootscript in my signature in code tags.

---

### Post by wilee-nilee on 2010-06-22
> **Alan Jack said:**
> Did exactly the same.

As best I can tell, its wiped the partition header for the linux partition, and I can't get anything to recover it.

GParted (running off the USB drive) is showing a 27 gig partition (which is mounted, and I've looked at, and it's Windows) and a 4.89 gig partition (which was hidden, I've un-hidden it, and its the recovery partition).  But between these is 117 gigs of an "unknown" partition.

I reinstall from factory default, but I'm on holiday and all my photos are in the unknown partition!!!

Help!

Have tried installing/running TestDisk, but it didn't seem to find anything.

Follow my instructions in post #3 in your own thread. These will not be the same so we always use separate threads in any problem.;)

---

### Post by aaroncam2 on 2010-06-22
I'm having issues with the boot script on the live usb cd its saved in 
/home/ubuntu/downloads
but when I try to run the command
```
sudo bash [/home/ubuntu/downloads]/boot_info_script055.sh
```Its saying there is no such file or directory. I'm following the directions inside the script. Thanks.

---

### Post by wilee-nilee on 2010-06-22
> **aaroncam2 said:**
> I'm having issues with the boot script on the live usb cd its saved in 
/home/ubuntu/downloads
but when I try to run the command
```
sudo bash [/home/ubuntu/downloads]/boot_info_script055.sh
```Its saying there is no such file or directory. I'm following the directions inside the script. Thanks.

Just copy and paste or drag it to the desktop and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```
From downloads the command is.
```
sudo bash ~/Downloads/boot_info_script*.sh
```

---

### Post by aaroncam2 on 2010-06-23
Here's the bootscript results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   167,782,859   167,782,797   7 HPFS/NTFS
/dev/sda2    *    302,246,910   312,496,379    10,249,470   c W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4         167,782,860   302,246,909   134,464,050  15 Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6C648DAC648D7A1A                       ntfs                                     
/dev/sda2        CCED-990E                              vfat       PE                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8CF7-0BB6                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```

---

### Post by aaroncam2 on 2010-06-24
i just decided to do a fresh install...thanks!

---

