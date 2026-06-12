---
title: "problems with wubi and boot"
date: 2010-07-17
forum: General Help
---

### Post by StuSchu on 2010-07-17
I'm running 9.10 on a Dell Inspiron Mini 10.  

When booting, before I get to the initial password screen, I receive  this message:

"One or more of the mounts listed in /etc/fstab  cannot be mounted:
/: waiting for /dev/loop0
/tmp: waiting for (null)
/boot: waiting for /host/ubuntu/disks/boot
Press ESC to enter a recovery shell"

Below is my Boot Info Script.  Is there someone out there who knows Wubi and can tell me what's wrong?


============================= Boot Info Summary:  ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdc

sda1: __________________________________________________   _______________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: __________________________________________________   _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr  /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: __________________________________________________   _______________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda3: __________________________________________________   _______________________

    File system:       vfat
    Boot sector type:  DEll Recovery: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sdc1: __________________________________________________   _______________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  __________________________________________________  ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell  Utility
/dev/sda2    *         96,390   292,109,894   292,013,505   7 HPFS/NTFS
/dev/sda3         292,109,895   312,576,704    20,466,810  db CP/M /  CTOS / ...


Drive: sdc ___________________  __________________________________________________  ___

Disk /dev/sdc: 4005 MB, 4005560320 bytes
16 heads, 32 sectors/track, 15280 cylinders, total 7823360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     7,823,359     7,823,328   c W95 FAT32  (LBA)


blkid -c /dev/null: __________________________________________________   __________

Device           UUID                                   TYPE       LABEL                          

/dev/loop0                                              squashfs                                  
/dev/loop1       8a08e272-916b-4188-b76e-5ad1334994aa   ext3                                      
/dev/sda1        07D9-0911                              vfat        DellUtility                   
/dev/sda2        42A689F6A689EB2D                       ntfs       OS                             
/dev/sda3        AC8B-6F35                              vfat        DELLRESTORE                   
/dev/sda: PTTYPE="dos" 
/dev/sdc1        1100-D9D3                              vfat        KINGSTON                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,i   ocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


==================== sda2/ubuntu/disks/boot/grub/menu.lst:  ====================

# menu.lst - See: grub(:cool:, info grub, update-grub(:cool:
#            grub-install(:cool:, grub-floppy(:cool:,
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from  0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default  entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the  default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive  editing
# control (menu entry editor and command-line)  and entries protected by  the
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
# kopt=root=UUID=42A689F6A689EB2D loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with  the
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
## update-grub will ignore non-xen kernels when running in domU and vice  versa
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

title        Ubuntu 9.10, kernel 2.6.31-22-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 9.10, kernel 2.6.31-21-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, kernel 2.6.28-17-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=42A689F6A689EB2D  loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.10, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the  Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux  OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux  OS
# on /dev/sda2
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,1)
savedefault
chainloader    +1


======================== sda2/ubuntu/winboot/menu.lst:  ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

================================ sda2/boot.ini:  ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOW  S 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Micro  soft Windows XP Home  Edition" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Ubuntu" 

=================== sda2: Location of files loaded by Grub:  ===================


    ??GB: ubuntu/disks/boot/grub/menu.lst
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-17-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-17-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-19-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-20-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-21-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-22-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-17-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-17-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-19-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-20-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-21-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-22-generic

============================= sda2/Wubi/etc/fstab:  =============================

# /etc/fstab: static file system  information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name  devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3     loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0        0
=========================== Unknown MBRs/Boot Sectors/etc  =======================

Unknown MBR on /dev/sda

00000000  b8 00 00 8e d0 bc 00 7c  8e d8 fc b9 80 00 8b f4   |.......|........|
00000010  bf 00 06 8e c0 f3 66 a5  ea 2d 06 00 00 10 00 01   |......f..-......|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 e8 c6 00   |................|
00000030  b4 11 cd 16 74 48 3d 00  89 75 43 b4 10 cd 16 33   |....tH=..uC....3|
00000040  db c6 87 be 07 00 80 bf  c2 07 db 74 0e 83 c3 10   |...........t....|
00000050  83 fb 40 72 ec be 48 07  e9 93 00 c6 87 be 07 80   |..@r..H.........|
00000060  c6 87 c2 07 0c 2e c7 06  21 06 00 06 b8 43 00 86   |........!....C..|
00000070  c4 b2 80 be 1d 06 cd 13  72 db 0a e4 75 d7 33 db   |........r...u.3.|
00000080  33 c9 8a 87 be 07 3c 00  74 0c 3c 80 74 05 be 8b   |3.....<.t.<.t...|
00000090  07 eb 5b 41 8b eb 83 c3  10 83 fb 40 72 e4 be 96   |..[A.......@r...|
000000a0  07 00 0c 80 f9 01 72 4c  77 44 be 59 07 8b c5 c1   |......rLwD.Y....|
000000b0  e8 04 00 44 1b 90 ff d7  66 8b 86 c6 07 66 2e a3   |...D....f....f..|
000000c0  25 06 2e c7 06 21 06 00  7c b4 42 b2 80 be 1d 06   |%....!..|.B.....|
000000d0  cd 13 be 81 07 72 17 0a  e4 75 13 be 79 07 ff d7   |.....r...u..y...|
000000e0  be ac 07 81 3e fe 7d 55  aa 75 03 e9 12 75 ff d7   |....>.}U.u...u..|
000000f0  b4 00 cd 16 cd 18 b8 03  00 cd 10 b8 00 b8 8e c0   |................|
00000100  33 ff b8 20 1f b9 50 00  f3 ab b1 0c be 3c 07 bf  |3..  ..P......<..|
00000110  44 00 ac ab e2 fc b4 02  b7 00 ba 00 02 cd 10 b4   |D...............|
00000120  86 b9 1e 00 ba 80 84 cd  15 bf 2d 07 c3 ac 3c 00   |..........-...<.|
00000130  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 77 77 77 2e   |t...........[www.|]("http://www.%7c/")
00000140  64 65 6c 6c 2e 63 6f 6d  43 61 6e 6e 6f 74 20 72   |dell.comCannot r|
00000150  65 73 74 6f 72 65 0d 0a  00 4c 6f 61 64 69 6e 67   |estore...Loading|
00000160  20 50 42 52 20 66 6f 72  20 64 65 73 63 72 69 70  | PBR for  descrip|
00000170  74 6f 72 20 31 2e 2e 2e  00 64 6f 6e 65 2e 0d 0a  |tor  1....done...|
00000180  00 66 61 69 6c 65 64 2e  0d 0a 00 42 61 64 20 66   |.failed....Bad f|
00000190  6c 61 67 0d 0a 00 30 20  61 63 74 69 76 65 20 70  |lag...0  active p|
000001a0  61 72 74 69 74 69 6f 6e  73 0d 0a 00 42 61 64 20   |artitions...Bad |
000001b0  50 42 52 0d 0a 00 00 00  a3 04 2d a4 00 00 00 01   |PBR.......-.....|
000001c0  01 00 de fe 3f 05 3f 00  00 00 47 78 01 00 80 00   |....?.?...Gx....|
000001d0  01 06 07 fe ff ff 86 78  01 00 c1 c5 67 11 00 fe   |.......x....g...|
000001e0  ff ff db fe ff ff 47 3e  69 11 7a 4c 38 01 00 00   |......G>i.zL8...|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa   |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard  drive==============

sdb

---

