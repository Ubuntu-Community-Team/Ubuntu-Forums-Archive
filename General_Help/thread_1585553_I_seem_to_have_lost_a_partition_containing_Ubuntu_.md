---
title: "I seem to have lost a partition containing Ubuntu 10.04 for no reason"
date: 2010-09-30
forum: General Help
---

### Post by Ray Hamilton on 2010-09-30
The other day when I started my desktop, up instead of getting my grub 2 menu offering Ubuntu 10.4, Ubuntu 9.04 and Vista (three of the main offerings anyway), all I got was the "grub-rescue> prompt".  I attempted a few things - basically re-installing grub and "update-grub" to what I incorrectly assumed was my 10.04 system partition.  This failed, which I see now is a result of the partition with 10.04 being missing. I  had not been doing anything to lose it such as playing with partitions or even installing anything.  Do you think there is an "easy" way to get the partition back - e.g. by changing the partition table.  Any ideas why this should have happened? Here is the result of running the boot-info script:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       151052287 sectors, but according to the info from 
                       fdisk, it has 151056383 sectors.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda6 starts at sector 474094278.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 555608088.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   172,024,019   151,050,452   7 HPFS/NTFS
/dev/sda3         172,025,856   323,082,239   151,056,384   7 HPFS/NTFS
/dev/sda4         323,084,286   625,137,344   302,053,059   f W95 Ext d (LBA)
/dev/sda5         398,588,778   474,094,214    75,505,437  83 Linux
/dev/sda6         474,094,278   549,615,779    75,521,502   b W95 FAT32
/dev/sda7         549,615,843   555,608,024     5,992,182  82 Linux swap / Solaris
/dev/sda8         555,608,088   625,137,344    69,529,257   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4013 MB, 4013948928 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             62     7,834,071     7,834,010   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       378bfd29-6597-4b61-ae8b-c42fcb782f14   ext3                                     
/dev/sda1        5402F9A402F98AEE                       ntfs       PQSERVICE                     
/dev/sda2        C224A94024A93875                       ntfs       VISTA                         
/dev/sda3        C224A94024A93875                       ntfs       Windows7                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        07d99973-de06-4643-82f9-081cef292145   ext3                                     
/dev/sda6        7753-A60B                              vfat                                     
/dev/sda7        915f374b-93e8-4d1e-b8e9-19d060ed6e4b   swap                                     
/dev/sda8        7850-7274                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdd1        4BBC-9F77                              vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=07d99973-de06-4643-82f9-081cef292145 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=07d99973-de06-4643-82f9-081cef292145

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		07d99973-de06-4643-82f9-081cef292145
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=07d99973-de06-4643-82f9-081cef292145 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		07d99973-de06-4643-82f9-081cef292145
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=07d99973-de06-4643-82f9-081cef292145 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Chainload into GRUB 2
root		07d99973-de06-4643-82f9-081cef292145
kernel		/boot/grub/core.img

title		Ubuntu 9.04, memtest86+
uuid		07d99973-de06-4643-82f9-081cef292145
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Recovery Partition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=07d99973-de06-4643-82f9-081cef292145 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=915f374b-93e8-4d1e-b8e9-19d060ed6e4b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 218.2GB: boot/grub/core.img
 218.1GB: boot/grub/menu.lst
 218.2GB: boot/grub/stage2
 218.1GB: boot/initrd.img-2.6.28-13-generic
 218.2GB: boot/vmlinuz-2.6.28-13-generic
 218.1GB: initrd.img
 218.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc

---

### Post by Ray Hamilton on 2010-10-04
Hold on to your seats - *bump*!

---

### Post by Rubi1200 on 2010-10-04
Are you able to boot into Windows normally?

And which partition was 10.04 supposed to be on?

You have GRUB2 installed in the MBR, but 9.04 on the partition (which uses the older version of GRUB).

Have you tried using Testdisk to recover the 10.04 partition?

---

### Post by Ray Hamilton on 2010-10-04
I am not able to boot into windows except by using Superdisk.

I am not sure which partition 10.04 was on.

I "accidentally" installed grub 2 on the 9.04 partition because I thought that it was 10.04!

Thanks for the pointer to testdisk.  I have googled it (I hate that expression) and will download and try it as soon as I get the time again.

Thanks again, and "I'll be back"

---

### Post by Rubi1200 on 2010-10-04
The first thing I would try is to reinstall the Windows bootloader.

To do this you need the Windows installation or recovery CD.

This guide outlines the process:

> [SIZE=5][COLOR=red]How to restore the Windows Vista or 7 bootloader[/COLOR][/SIZE]

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7  installation disk, you can get the same effect with a Vista recovery  disk, which you can download for [Vista]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download") or [Win 7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/").
When you get to the Regional settings, select your Location/Keyboard  setting then click next. On the next page you must click on "Repair your  computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

 	Code:
 	bootrec.exe /fixboot 
 	Code:
 	bootrec.exe /fixmbr 
Now close the two windows and click "Restart."

Take out your Vista/7 DVD and hopefully, you will be left with your Windows Vista/7 Bootloader.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Once you can boot into Windows normally again, we can take it from there.

---

### Post by Ray Hamilton on 2010-10-05
Ok. I have downloaded and burnt a CD (long story in itself, but never mind). I have booted the PC using the disk and I have followed the instructions up to "click repair".  However, before I can get to the point where I need to ensure that my installation is not selected ,a System Recovery Options windows reports: "Windows found problems with your computer's startup options. Do you want to apply repairs and restart your computer" There is a view details option which basically says that the following startup options will be added ... and it includes a Windows device: Partition=F (73758 MB).
So my question really is: Is there a step missing from the instructions and should I select No ?

Edit:
I was being (overly) cautious.  Yes it appears there is a step missing or I am reading the instructions wrongly.  On the above option, select NO.  Then you get a chance to Choose a recovery tool.  The bottom option is "Command prompt"

My new question is should I still use the command prompt option or would the Start Repair option have sufficed?  (Sorry to be cautious but I would prefer not to lose any data etc.)

---

### Post by Rubi1200 on 2010-10-05
Correct, leave whatever it finds UNSELECTED and pick the command prompt option.

Then type:
```
bootrec.exe /fixboot
``` and 
```
bootrec.exe /fixmbr

```Close the windows and click Restart.

Hopefully, that will get you back into Windows.

As far as data is concerned, you should have tried to backup everything already. 

I suspect the Ubuntu partition is gone, but let's get you back into Windows first.

If this works, use an Ubuntu CD and post the results of the boot-script again (in other words, the results should be different from the first time).

---

### Post by oldfred on 2010-10-05
You are showing two vfat partitions sda6 & sda8, were these always FAT32 or did they somehow get converted and were your 10.04 install?

Testdisk should be able to tell if partition was changed as it seems to find the history and let you recover.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by Ray Hamilton on 2010-10-05
Oldfred:
I am ashamed to say that I cannot remember what was on each partition (on my previous PC I had a record of what was what)! I remember that initially it was around 160Gb of which 10 Gb was for a recovery partition.  I then split the remaining into 4: 1 for the original Vista, one containing a copy of Vista ready for an upgrade to Windows 7 (which I still have not done, over half a year later), one for Ubuntu 9.04 and the other left empty to experiment with - this became 10.04 a few months ago, and I was fairly happy with it.  I know I was going to have a partition to be used as a common area for data to be shared between OSs but I can't remember if I did it. That was a long way of saying I don't know, wasn't it?
Hope you are right about testdisk. I'm hoping it won't be affected by rescuing Windows

---

### Post by Ray Hamilton on 2010-10-06
Rubi1200, I have followed your instructions and the PC boots straight into Vista.  Thanks.  I await your further instructions to hopefully restore everything else!!

---

### Post by Rubi1200 on 2010-10-06
Well, I am really pleased that at least one issue has been resolved :)

Please use an Ubuntu CD to boot the computer and post the results of the boot-script again with the new situation so we can re-evaluate what the next steps might be.

Thanks.

---

### Post by Ray Hamilton on 2010-10-06
Here are the results of running the script now:

By the way I found some notes that said when I was setting things up, that I formatted 2 partitions as Fat32 to enable recognition by Gparted. I used these for Ubuntu installations.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       151052287 sectors, but according to the info from 
                       fdisk, it has 151056383 sectors.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda6 starts at sector 474094278.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda8 starts at sector 555608088.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   172,024,019   151,050,452   7 HPFS/NTFS
/dev/sda3         172,025,856   323,082,239   151,056,384   7 HPFS/NTFS
/dev/sda4         323,084,286   625,137,344   302,053,059   f W95 Ext d (LBA)
/dev/sda5         398,588,778   474,094,214    75,505,437  83 Linux
/dev/sda6         474,094,278   549,615,779    75,521,502   b W95 FAT32
/dev/sda7         549,615,843   555,608,024     5,992,182  82 Linux swap / Solaris
/dev/sda8         555,608,088   625,137,344    69,529,257   b W95 FAT32


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4013 MB, 4013948928 bytes
124 heads, 62 sectors/track, 1019 cylinders, total 7839744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             62     7,834,071     7,834,010   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       378bfd29-6597-4b61-ae8b-c42fcb782f14   ext3                                     
/dev/sda1        5402F9A402F98AEE                       ntfs       PQSERVICE                     
/dev/sda2        C224A94024A93875                       ntfs       VISTA                         
/dev/sda3        C224A94024A93875                       ntfs       Windows7                      
/dev/sda4: PTTYPE="dos" 
/dev/sda5        07d99973-de06-4643-82f9-081cef292145   ext3                                     
/dev/sda6        7753-A60B                              vfat                                     
/dev/sda7        915f374b-93e8-4d1e-b8e9-19d060ed6e4b   swap                                     
/dev/sda8        7850-7274                              vfat                                     
/dev/sda: PTTYPE="dos" 
/dev/sdd1        4BBC-9F77                              vfat                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=07d99973-de06-4643-82f9-081cef292145 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=07d99973-de06-4643-82f9-081cef292145

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		07d99973-de06-4643-82f9-081cef292145
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=07d99973-de06-4643-82f9-081cef292145 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		07d99973-de06-4643-82f9-081cef292145
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=07d99973-de06-4643-82f9-081cef292145 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Chainload into GRUB 2
root		07d99973-de06-4643-82f9-081cef292145
kernel		/boot/grub/core.img

title		Ubuntu 9.04, memtest86+
uuid		07d99973-de06-4643-82f9-081cef292145
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Recovery Partition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=07d99973-de06-4643-82f9-081cef292145 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=915f374b-93e8-4d1e-b8e9-19d060ed6e4b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 218.2GB: boot/grub/core.img
 218.1GB: boot/grub/menu.lst
 218.2GB: boot/grub/stage2
 218.1GB: boot/initrd.img-2.6.28-13-generic
 218.2GB: boot/vmlinuz-2.6.28-13-generic
 218.1GB: initrd.img
 218.2GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc

---

### Post by oldfred on 2010-10-06
You cannot install Ubuntu into FAT32 partitions. Either you never installed, but thought you did? Or the partitions somehow reverted and testdisk should show that in it's history. Did you try the testdisk, you can run from the liveCD but have to download it and add to sources either universe or restricted for it to download it.

---

### Post by Ray Hamilton on 2010-10-06
Oldfred: 
Yes I know I cannot install Ubuntu into Fat32, I was simply giving this as added information with regard to your post.  I have tried to try testdisk! However I am using a USB to boot Ubuntu and it has run out of room!  I think I have a few files that I can delete from it (or transfer to windows), mainly GO books that I can download again anyway. I did try to download from the repositories but even after adding universe it wasn't found in Ubuntu Software or Synaptic manager, so I was downloading it from [www.cgsecurity.org](www.cgsecurity.org)  I'll give this a try again tomorrow - my computer time has run out, according to my wife!

---

### Post by Ray Hamilton on 2010-10-07
I've managed to locate my LiveCD and downloaded testdisk, but it seems a little complicated and I'm too tired to work it out (if I even can when I'm not tired).  Anyone able to assist me here?

---

### Post by Ray Hamilton on 2010-10-10
I downloaded the Windows version of testdisk and ran it. I used the "Analyse" option, This seemed to find all the partitions and I checked that sda5 had the Ubuntu 10.04.  This was correct, so I used the write option to put the changes back to disk.  I re-installed grub2 to sda5 and VOILA - success :guitar:.  Everything seems to be back as it was.  I am going to make a note of the partition set up and maybe make a backup.

Thanks guys for the pointer to testdisk - a great utility that will be added to my arsenal of tools. :P

---

