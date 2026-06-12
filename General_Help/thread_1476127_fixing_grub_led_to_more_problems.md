---
title: "fixing grub led to more problems"
date: 2010-05-07
forum: General Help
---

### Post by diddybones on 2010-05-07
i was running linux 9.10, on a seperate partition i installed windows 7.
 
This led to the issue where i cannot select os's at boot up
 
so i follow instruction in here..
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
ive obviously done something wrong
 
 In the end i  used the "super grub disk" on the manual setting to see if i could boot in to my partition ubuntu there. i get to the os selection and get this error when i try the top one. i get a slightly different error in each ubuntu option in the menu ...(recovery mode etc)
 
error
-------------------------------------------------------------------------------------------------
 
kernal /boot/vmlinuz-2.6.31.20.generic root= UUID 94fe7374-74c9-4909-b4f7-58e5c-8cb51 ro quiet splash
 
error 15
 
file not found
-------------------------------------------------------------------------------------------
 
How damaged is this? what can i do
 
thanks

---

### Post by zuerston on 2010-05-07
> **diddybones said:**
> i was running linux 9.10, on a seperate partition i installed windows 7.
 
This led to the issue where i cannot select os's at boot up
 
so i follow instruction in here..
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
ive obviously done something wrong
 
 In the end i  used the "super grub disk" on the manual setting to see if i could boot in to my partition ubuntu there. i get to the os selection and get this error when i try the top one. i get a slightly different error in each ubuntu option in the menu ...(recovery mode etc)
 
error
-------------------------------------------------------------------------------------------------
 
kernal /boot/vmlinuz-2.6.31.20.generic root= UUID 94fe7374-74c9-4909-b4f7-58e5c-8cb51 ro quiet splash
 
error 15
 
file not found
-------------------------------------------------------------------------------------------
 
How damaged is this? what can i do
 
thanks

Sounds like you did a number on your MBR boot sector.
Did you read this part first?

------
**Introduction**

 This method will install Grub  bootloader into the [Master Boot  Record (MBR)]("http://en.wikipedia.org/wiki/Master_boot_record") of the main computer hard drive. 
The slight complexity of this method consists of  determining whether Ubuntu Operating System installed on your computer  was configured for Grub or Grub 2. 

[LIST]
[*]If  you fresh-installed Ubuntu Karmic 9.10 or newer, you are running **[Grub2]("https://help.ubuntu.com/community/Grub2")**.   
[*]If  you ran previous version of Ubuntu and upgraded to Ubuntu Karmic 9.10,  you are running **[Grub Legacy]("https://help.ubuntu.com/community/GrubHowto")**  by default; unless you have executed upgrade-from-grub-legacy, then you  are running **[Grub2]("https://help.ubuntu.com/community/Grub2")**.  
[*]If you are running Ubuntu Jaunty, you are running **[Grub Legacy]("https://help.ubuntu.com/community/GrubHowto")**.  
[*]If you are not  sure, follow the guide assuming you are running Grub2 -- there will be a  point to make a correction. 
[/LIST]
 
**Create and boot from a Live  CD**


------------------------
Its a good time to junk Windows and do a 10.4 install and move on forward!):P

---

### Post by diddybones on 2010-05-07
hi 
 
yeah im using grub legacy...
 
I made a livecd, ran that, and got in to the "try ubuntu" part and followed the instructions there
 
the erro happened after all of that..
 
my concern is getting access to all my "stuff" on the  ubuntu i cant open
 
thanks for the help

---

### Post by oldfred on 2010-05-07
Usually error 15 relates to having both old grub legacy and grub2 conflicting with each other. Often have to uninstall both and reinstall one. To see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by diddybones on 2010-05-09
Hi im not sure i managed the code tags?.... thanks for the help

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 353786831 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sdb has 
                       1946048 sectors.. But according to the info from the 
                       partition table , it has 15568392 sectors.
    Mounting failed:
mount: /dev/sdb already mounted or FD/sdb busy

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26c326c3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    64,002,959    64,002,897   7 HPFS/NTFS
/dev/sda2          64,002,960   625,137,344   561,134,385   5 Extended
/dev/sda5          64,003,023   603,963,674   539,960,652  83 Linux
/dev/sda6         603,963,738   625,137,344    21,173,607  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B0B6D265B6D22C1A                       ntfs                                     
/dev/sda5        94fe7374-7fc9-4909-b4f7-58e5c8cb1951   ext3                                     
/dev/sda6        b42c2b2c-c20b-48af-8da4-f0641b3669ed   swap                                     
/dev/sdb1        3141-5926                              vfat       ECKELLY'S I                   
/dev/sdb         A88B-3652                              vfat       iPod                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/ECKELLY'S I       vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=94fe7374-7fc9-4909-b4f7-58e5c8cb1951 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=94fe7374-7fc9-4909-b4f7-58e5c8cb1951

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

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        94fe7374-7fc9-4909-b4f7-58e5c8cb1951
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=94fe7374-7fc9-4909-b4f7-58e5c8cb1951 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        94fe7374-7fc9-4909-b4f7-58e5c8cb1951
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=94fe7374-7fc9-4909-b4f7-58e5c8cb1951 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        94fe7374-7fc9-4909-b4f7-58e5c8cb1951
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=94fe7374-7fc9-4909-b4f7-58e5c8cb1951 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        94fe7374-7fc9-4909-b4f7-58e5c8cb1951
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=94fe7374-7fc9-4909-b4f7-58e5c8cb1951 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, memtest86+
uuid        94fe7374-7fc9-4909-b4f7-58e5c8cb1951
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1


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
UUID=94fe7374-7fc9-4909-b4f7-58e5c8cb1951 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b42c2b2c-c20b-48af-8da4-f0641b3669ed none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 181.1GB: boot/grub/menu.lst
 181.1GB: boot/grub/stage2
 181.2GB: boot/initrd.img-2.6.31-19-generic
 181.1GB: boot/initrd.img-2.6.31-20-generic
 181.1GB: boot/vmlinuz-2.6.31-19-generic
 181.1GB: boot/vmlinuz-2.6.31-20-generic
 181.1GB: initrd.img
 181.2GB: initrd.img.old
 181.1GB: vmlinuz
 181.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by oldfred on 2010-05-09
Even though you have 9.10 it must be an upgrade as upgrades kept the  grub legacy from the previous install. Only new installs of 9.10 have grub2.

You currently have the windows boot in the MBR and if you want to boot Ubuntu you will need to install grub legacy (0.97). Follow directions of old grub not grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

