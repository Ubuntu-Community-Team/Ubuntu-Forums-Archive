---
title: "Need urgent help fixing grub 1.5"
date: 2010-02-04
forum: General Help
---

### Post by aviramof on 2010-02-04
i have just discoverd i can't enter my windows 7 via grub boot menu i get error 13
**Invalid or unsupported executable format**
**what can i do?**
 
is there something wrong here like the map part?
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows 7 (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
 
thanks in advance.
 
here is a resault.txt file:
 
```
============================= Boot Info Summary: ==============================
 
 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________
 
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
 
sda2: _________________________________________________________________________
 
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
 
sdb1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr
 
sdb2: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
sdb3: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ _____________________________________________________
 
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90d490d4
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sda1    *             63    29,993,354    29,993,292  83 Linux
/dev/sda2          29,993,355    34,089,929     4,096,575  82 Linux swap / Solaris
 
 
Drive: sdb ___________________ _____________________________________________________
 
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26ff26fe
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sdb1    *             63    78,156,224    78,156,162   7 HPFS/NTFS
/dev/sdb2          78,157,824   162,043,903    83,886,080   7 HPFS/NTFS
/dev/sdb3         162,043,904   312,577,499   150,533,596   7 HPFS/NTFS
 
 
blkid -c /dev/null: ____________________________________________________________
 
Device           UUID                                   TYPE       LABEL                         
 
/dev/sda1        90ac6c9d-2c23-49f5-a8b2-42f2efd62ced   ext3                                     
/dev/sda2        badd69a7-849b-44e5-b1fc-050abc7653bb   swap                                     
/dev/sdb1        C44451F64451EC24                       ntfs       Windows 7                     
/dev/sdb2        58544AAE544A8F26                       ntfs       Log1 sda1 sda2 sdb1 BLKID Trash
/dev/sdb2        58544AAE544A8F26                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
/dev/sdb3        EA9635979635656B                       ntfs       Log1 sda1 sda2 sdb1 sdb2 BLKID Trash
/dev/sdb3        EA9635979635656B                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
 
============================ "mount | grep ^/dev  output: ===========================
 
Device           Mount_Point              Type       Options
 
/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
 
 
=========================== sda1/boot/grub/menu.lst: ===========================
 
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
default        6
 
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10
 
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
 
# Pretty colours
color cyan/blue white/blue
 
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
# kopt=root=UUID=90ac6c9d-2c23-49f5-a8b2-42f2efd62ced ro
 
## default grub root device
## e.g. groot=(hd0,0)
# groot=90ac6c9d-2c23-49f5-a8b2-42f2efd62ced
 
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
 
title        Ubuntu 8.10, kernel 2.6.27-16-generic
uuid        90ac6c9d-2c23-49f5-a8b2-42f2efd62ced
kernel        /boot/vmlinuz-2.6.27-16-generic root=UUID=90ac6c9d-2c23-49f5-a8b2-42f2efd62ced ro quiet splash 
initrd        /boot/initrd.img-2.6.27-16-generic
quiet
 
title        Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
uuid        90ac6c9d-2c23-49f5-a8b2-42f2efd62ced
kernel        /boot/vmlinuz-2.6.27-16-generic root=UUID=90ac6c9d-2c23-49f5-a8b2-42f2efd62ced ro  single
initrd        /boot/initrd.img-2.6.27-16-generic
 
title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        90ac6c9d-2c23-49f5-a8b2-42f2efd62ced
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=90ac6c9d-2c23-49f5-a8b2-42f2efd62ced ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet
 
title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        90ac6c9d-2c23-49f5-a8b2-42f2efd62ced
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=90ac6c9d-2c23-49f5-a8b2-42f2efd62ced ro  single
initrd        /boot/initrd.img-2.6.27-7-generic
 
title        Ubuntu 8.10, memtest86+
uuid        90ac6c9d-2c23-49f5-a8b2-42f2efd62ced
kernel        /boot/memtest86+.bin
quiet
 
### END DEBIAN AUTOMAGIC KERNELS LIST
 
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root
 
 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows 7 (loader)
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
 
 
=============================== sda1/etc/fstab: ===============================
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=90ac6c9d-2c23-49f5-a8b2-42f2efd62ced /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=badd69a7-849b-44e5-b1fc-050abc7653bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
 
Nevermind problem solved changed root (hd1,0) to root (hd0,0)

---

### Post by meierfra. on 2010-02-04
It seems your bios are booting from your 160GB  Windows hard drive. So see what happens if you set your bios to boot from the 82GB Ubuntu hard drive.

---

