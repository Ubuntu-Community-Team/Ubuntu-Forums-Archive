---
title: "Help, Can't BOOTGrub2"
date: 2010-06-01
forum: General Help
---

### Post by rodh on 2010-06-01
Help Please, I was upgrading From Grub Legacyto Grub2 now I can not boot. Super Grub Disk did not help, Booting from Live CD

Files that might help;

rod@rod-desktop:~$ sudo fdisk -l
[sudo] password for rod: 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000900cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c96ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       38428       38913     3903795   82  Linux swap / Solaris
/dev/sdb2               1       38427   308664846    5  Extended
/dev/sdb5               1       18665   149926549+  83  Linux
/dev/sdb6           18666       37732   153155646   83  Linux
/dev/sdb7           37733       38427     5582556   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 16.0 GB, 16026435072 bytes
64 heads, 32 sectors/track, 15283 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00002220

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       15283    15649776    c  W95 FAT32 (LBA)
rod@rod-desktop:~$ 

----------------------------------------------------------------------------------------------------------------------------------------------

rod@rod-desktop:~$ sudo blkid
/dev/sda1: UUID="5b5a6c51-edae-4266-88c6-c89ea2e3f736" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="01e58d99-066e-462a-a663-e2842a14383b" TYPE="swap" 
/dev/sdb5: UUID="ae5d4997-4763-473e-89fa-50f1eb72bf30" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb6: UUID="3d10019e-9068-4fd7-b72f-47dfea048e95" TYPE="ext3" 
/dev/sdb7: UUID="2d1d476e-e631-4dfb-8d88-c4899756651c" TYPE="swap" 
/dev/sdc1: LABEL="BACKUP THUM" UUID="97C1-D002" TYPE="vfat" 
rod@rod-desktop:~$

---

### Post by KermEd on 2010-06-01
Hmm...

Bare with me but - below are some suggestions I can think of.

Error 15 means it can't find a file - but usually the partitions themselves are in-tact.  

When you boot from your live CD, can you get a list of what 'should' be there for your boot files?

> cd /boot
lsIf the Kernels are in-tact - the following should rebuild the Grub menu for you, 

> update-grub2And last, at the boot menu when you see:

Error 15: File not found
Press any key to continue..

After pressing that key it should spit out some more information that might be helpful.  

- Lloyd

---

### Post by rodh on 2010-06-01
I amnot getting error anymore just blinking cousor

---

### Post by drs305 on 2010-06-01
rodh,

Please post the contents of the boot info script (between code tags) so we can take a look at your current setup:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by rodh on 2010-06-02
here is the results of Boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSDOS5.0: Fat 16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c96ff

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    617,329,755   625,137,344     7,807,590  82 Linux swap / Solaris
/dev/sda2                  63   617,329,754   617,329,692   5 Extended
/dev/sda5                 126   299,853,224   299,853,099  83 Linux
/dev/sda6         299,853,288   606,164,579   306,311,292  83 Linux
/dev/sda7         606,164,643   617,329,754    11,165,112  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000900cc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   490,223,474   490,223,412  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 245     1,999,871     1,999,627   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01e58d99-066e-462a-a663-e2842a14383b   swap                                     
/dev/sda5        ae5d4997-4763-473e-89fa-50f1eb72bf30   ext3                                     
/dev/sda6        3d10019e-9068-4fd7-b72f-47dfea048e95   ext3                                     
/dev/sda7        2d1d476e-e631-4dfb-8d88-c4899756651c   swap                                     
/dev/sdb1        5b5a6c51-edae-4266-88c6-c89ea2e3f736   ext3                                     
/dev/sdc1        3B69-1AFD                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)
/dev/sda6        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda5        /media/disk-2            ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1        /media/disk-3            ext3       (rw,nosuid,nodev,uhelper=hal)


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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ae5d4997-4763-473e-89fa-50f1eb72bf30

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=5b5a6c51-edae-4266-88c6-c89ea2e3f736 /home           ext3    relatime        0       2
# swap was on /dev/sda1 during installation
UUID=01e58d99-066e-462a-a663-e2842a14383b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 134.4GB: boot/grub/menu.lst
 134.4GB: boot/grub/stage2
 134.4GB: boot/initrd.img-2.6.28-11-generic
 134.4GB: boot/initrd.img-2.6.28-15-generic
 134.4GB: boot/vmlinuz-2.6.28-11-generic
 134.4GB: boot/vmlinuz-2.6.28-15-generic
 134.4GB: initrd.img
 134.4GB: initrd.img.old
 134.4GB: vmlinuz
 134.4GB: vmlinuz.old

=========================== sda6/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        6

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3d10019e-9068-4fd7-b72f-47dfea048e95

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
# defoptions=vga=788 splash

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-18-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-18-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-16-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-15-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-15-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=6
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-19-generic ...'
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-18-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-18-generic ...'
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-17-generic ...'
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-16-generic ...'
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-15-generic ...'
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.28-16-generic ...'
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.28-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.28-15-generic ...'
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.28-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.28-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.28-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.28-11-generic ...'
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.28-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2d1d476e-e631-4dfb-8d88-c4899756651c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 301.8GB: boot/grub/core.img
 301.8GB: boot/grub/grub.cfg
 301.8GB: boot/grub/menu.lst
 301.8GB: boot/initrd.img-2.6.28-11-generic
 301.8GB: boot/initrd.img-2.6.28-15-generic
 301.8GB: boot/initrd.img-2.6.28-16-generic
 301.8GB: boot/initrd.img-2.6.31-14-generic
 301.7GB: boot/initrd.img-2.6.31-15-generic
 301.8GB: boot/initrd.img-2.6.31-16-generic
 301.8GB: boot/initrd.img-2.6.31-17-generic
 301.7GB: boot/initrd.img-2.6.31-18-generic
 301.8GB: boot/initrd.img-2.6.31-19-generic
 301.8GB: boot/initrd.img-2.6.31-20-generic
 301.8GB: boot/initrd.img-2.6.31-21-generic
 301.9GB: boot/initrd.img-2.6.32-22-generic
 301.7GB: boot/vmlinuz-2.6.28-11-generic
 301.7GB: boot/vmlinuz-2.6.28-15-generic
 301.7GB: boot/vmlinuz-2.6.28-16-generic
 301.7GB: boot/vmlinuz-2.6.31-14-generic
 301.8GB: boot/vmlinuz-2.6.31-15-generic
 301.7GB: boot/vmlinuz-2.6.31-16-generic
 301.7GB: boot/vmlinuz-2.6.31-17-generic
 301.7GB: boot/vmlinuz-2.6.31-18-generic
 301.7GB: boot/vmlinuz-2.6.31-19-generic
 301.8GB: boot/vmlinuz-2.6.31-20-generic
 301.7GB: boot/vmlinuz-2.6.31-21-generic
 301.8GB: boot/vmlinuz-2.6.32-22-generic
 301.9GB: initrd.img
 301.8GB: initrd.img.old
 301.8GB: vmlinuz
 301.7GB: vmlinuz.old

================================ sdc1/menu.lst: ================================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        6

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3d10019e-9068-4fd7-b72f-47dfea048e95

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
# defoptions=vga=788 splash

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-18-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-18-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-16-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-15-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-15-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: menu.lst
```

---

### Post by drs305 on 2010-06-02
It appears that 10.04 on sda6 is the installation you mostly likely want to use.

If that is the case, boot from the Lucid LiveCD, open a terminal, and install Grub2. You want Grub2 installed on the MBR of **sda** *drive*. It will automatically place it's boot files in the partition of sda6 and you don't need to select it during the installation if you run the following:

[COLOR="Red"]Edited:[/COLOR]
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot and it should run 10.04 installed on sda6.

The next issue, *if the above is successful*, would be to remove some of the older kernels. Unless you have a specific need or desire to keep old ones, they really don't add anything and really clutter up your menu. This is a personal choice, but if you want to remove them I highly recommend using Ubuntu Tweak. You might want to keep one extra older kernel as a 'backup' and remove the rest in each release. 

For details on how to remove older kernels, refer to "Removing Older Kernels" section of this thread. Be sure to read the Ubuntu Tweak paragraphs.
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by yetiman64 on 2010-06-02
@ drs305, Correct me if I'm wrong but won't your second command,
> sudo grub-install --root-directory=/mnt /dev/sda6 try to install grub bootloader to the sda6 partition and not the MBR of sda. I have run into problems with loading grub2 to a partition recently. Please check.

---

### Post by drs305 on 2010-06-02
> **yetiman64 said:**
> @ drs305, Correct me if I'm wrong but won't your second command,
 try to install grub bootloader to the sda6 partition and not the MBR of sda. I have run into problems with loading grub2 to a partition recently. Please check.

You are absolutely correct. I had sda**6** on my brain it appears.  I've edited it. Thanks.

---

### Post by yetiman64 on 2010-06-02
@drs305
You're welcome and thanks for writing the grub2 guide, I've been virtually "living" on that thread recently. Cheers.

---

### Post by rodh on 2010-06-02
Great,  Thanks I'm back on.  But back to where I started this odyssey,  still chain loading from grub-->grub2 and when I ran the upgrade command that is suggested in grub legacy I lost it.  And if I remember right during the 9.04 install (which is the last CD install) I had problems and had to identify the boot disk by uuid.  I do not remember how this is done and was unable to locate the info,  ie. forum that I used to get through it.  I am not sure which forum that I was on at the time,

---

### Post by drs305 on 2010-06-02
What is your boot status at the moment? Are you back to Grub/Grub2 Chainload then? If the info in the boot info script has changed, please run it again.

You mentioned UUIDs. Sometimes people had to remove the UUID and replace it with root=/dev/sdaX in the "linux" line of Grub2 and also remove the "search" line, which also had the UUIDs listed. From a Grub 2 menu, you would manually edit them by highlighting the choice, then pressing "e" to get into the edit mode. For the above, you would hold down the DEL key on the "search" line to remove it, and the arrow keys to replace the root=UUID with root=/dev/sdaX.

But that may be a bit ahead of where we are. If you want to continue to upgrade to G2, answer the first two questions and we can see where we are.

---

### Post by rodh on 2010-06-02
Boots good,  Grub-->Grub2-->10.04 System comes up just fine. 
Here is new Boot-Script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSDOS5.0: Fat 16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   490,223,474   490,223,412  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *    617,329,755   625,137,344     7,807,590  82 Linux swap / Solaris
/dev/sdb2                  63   617,329,754   617,329,692   5 Extended
/dev/sdb5                 126   299,853,224   299,853,099  83 Linux
/dev/sdb6         299,853,288   606,164,579   306,311,292  83 Linux
/dev/sdb7         606,164,643   617,329,754    11,165,112  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders, total 2001888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 245     1,999,871     1,999,627   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5b5a6c51-edae-4266-88c6-c89ea2e3f736   ext3                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        01e58d99-066e-462a-a663-e2842a14383b   swap                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        ae5d4997-4763-473e-89fa-50f1eb72bf30   ext3                                     
/dev/sdb6        3d10019e-9068-4fd7-b72f-47dfea048e95   ext3                                     
/dev/sdb7        2d1d476e-e631-4dfb-8d88-c4899756651c   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3B69-1AFD                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb6        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sdb5/boot/grub/menu.lst: ===========================

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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ae5d4997-4763-473e-89fa-50f1eb72bf30

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ae5d4997-4763-473e-89fa-50f1eb72bf30
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=5b5a6c51-edae-4266-88c6-c89ea2e3f736 /home           ext3    relatime        0       2
# swap was on /dev/sda1 during installation
UUID=01e58d99-066e-462a-a663-e2842a14383b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 134.4GB: boot/grub/menu.lst
 134.4GB: boot/grub/stage2
 134.3GB: boot/initrd.img-2.6.28-11-generic
 134.4GB: boot/initrd.img-2.6.28-15-generic
 134.4GB: boot/vmlinuz-2.6.28-11-generic
 134.4GB: boot/vmlinuz-2.6.28-15-generic
 134.4GB: initrd.img
 134.3GB: initrd.img.old
 134.4GB: vmlinuz
 134.4GB: vmlinuz.old

=========================== sdb6/boot/grub/menu.lst: ===========================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        6

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3d10019e-9068-4fd7-b72f-47dfea048e95

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
# defoptions=vga=788 splash

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-18-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-18-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-16-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-15-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-15-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=========================== sdb6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,6)'
search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro splash quiet vga=794  quiet splash nomodeset video=uvesafb:mode_option=1680x1050-24,mtrr=3,scroll=ywrap
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single splash quiet vga=794
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,6)'
    search --no-floppy --fs-uuid --set 3d10019e-9068-4fd7-b72f-47dfea048e95
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set ae5d4997-4763-473e-89fa-50f1eb72bf30
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2d1d476e-e631-4dfb-8d88-c4899756651c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 301.8GB: boot/grub/core.img
 301.7GB: boot/grub/grub.cfg
 301.8GB: boot/grub/menu.lst
 301.7GB: boot/grub/stage2
 301.8GB: boot/initrd.img-2.6.31-20-generic
 301.8GB: boot/initrd.img-2.6.31-21-generic
 301.9GB: boot/initrd.img-2.6.32-22-generic
 301.8GB: boot/vmlinuz-2.6.31-20-generic
 301.7GB: boot/vmlinuz-2.6.31-21-generic
 301.8GB: boot/vmlinuz-2.6.32-22-generic
 301.9GB: initrd.img
 301.8GB: initrd.img.old
 301.8GB: vmlinuz
 301.7GB: vmlinuz.old

================================ sdc1/menu.lst: ================================

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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        6

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3d10019e-9068-4fd7-b72f-47dfea048e95

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
# defoptions=vga=788 splash

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-20-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-19-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-18-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-18-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-17-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-16-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-16-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-15-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-15-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-14-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-15-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro vga=788 splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3d10019e-9068-4fd7-b72f-47dfea048e95 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        3d10019e-9068-4fd7-b72f-47dfea048e95
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single 
initrd        /boot/initrd.img-2.6.28-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae5d4997-4763-473e-89fa-50f1eb72bf30 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title        Ubuntu 9.04, memtest86+ (on /dev/sda5)
root        (hd0,4)
kernel        /boot/memtest86+.bin  
savedefault
boot


=================== sdc1: Location of files loaded by Grub: ===================


    ??GB: menu.lst
```

---

### Post by oldfred on 2010-06-02
Are you booting from the 250 sda or 320GB sdb? Even though the script says the grub2 in sda boots the same drive I have seen that either grub or the script mis-report that. I would think if you choose to boot the 250
GB drive in BIOS it will boot grub2 directly.

If it works I would still consider installing grub2 to the MBR of sdb as it is better to have to boot loader on the same drive as the install.

---

### Post by rodh on 2010-06-03
[SIZE=4]OK,  I set the BIOS to boot the 250 GB sdb and now Grub2 is the only boot loader that comes up and it boots into 10.04 much faster.  I would say that you a a genius,  Thank you for your time and effort.  I really should work with this more but I find that Ubuntu doesn't need much tweaking to do what I need after the initial set up has been accomplished.  And then I get lazy and just leave it alone until the next update or upgrade that bonks the system again.    [/SIZE]:)

---

