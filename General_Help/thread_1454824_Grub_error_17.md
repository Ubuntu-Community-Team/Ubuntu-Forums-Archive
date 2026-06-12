---
title: "Grub error 17"
date: 2010-04-15
forum: General Help
---

### Post by dazzyuk on 2010-04-15
There are loads of threads on this but each one seems to say something different and I do not know which one I should try as I do not want to damage my system any further. 

I created a new ext3 partition in Windows and then after a reboot I got an error 17 with grub, I have since deleted that with Gparted from the live USB and resized my drive so Ubuntu has more space, can anyone suggest a way to fix this?

I have the following in Gparted:

/dev/sda1 - NTFS

/dev/sda2 - extended
/dev/sda6 - ext3
/dev/sda7 - linux-swap
/dev/sda5 - linux-swap

---

### Post by prodigy_ on 2010-04-15
Boot from Ubuntu Live CD and run [this script](http://bootinfoscript.sourceforge.net/). Post the output here.

---

### Post by dazzyuk on 2010-04-15
ok here are the results:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /wubildr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc: _________________________________________________________________________

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
Disk identifier: 0xa42d04a3

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   276,221,609   276,221,547   7 HPFS/NTFS
/dev/sda2         276,221,610   312,576,704    36,355,095   5 Extended
/dev/sda5         306,616,653   312,576,704     5,960,052  82 Linux swap / Solaris
/dev/sda6         276,221,736   306,263,159    30,041,424  83 Linux
/dev/sda7         306,263,223   306,616,589       353,367  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1039 MB, 1039663104 bytes
32 heads, 62 sectors/track, 1023 cylinders, total 2030592 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0001dc16

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             62     2,029,631     2,029,570   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FE6438A164385F19                       ntfs                                     
/dev/sda5        baa8e287-e33e-4875-a2a5-7d659f0b52b5   swap                                     
/dev/sda6        083c1e3b-16ee-4c0c-89e9-abb281288fdf   ext3                                     
/dev/sda7        cf60af86-e459-474f-a865-8c0150546c81   swap                                     
/dev/sdc         7C85-9E85                              vfat                                     
/dev/sdd1        6CE1-6634                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sdc         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


======================== sda1/ubuntu/winboot/menu.lst: ========================

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

================================ sda1/boot.ini: ================================

[Boot Loader]
Timeout=10
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[Operating Systems]
C:\btsec\XPSTP.bs="1. Begin TXT Mode Setup Windows XP, Never unplug USB-Drive Until Logon"
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="2. and 3. Continue with GUI Mode Setup Windows XP + Start XP from HD 1" /FASTDETECT
multi(0)disk(0)rdisk(2)partition(1)\WINDOWS="Continue GUI Setup + Start XP from HD 2, use if installing on HD2" /FASTDETECT
c:\grldr="4. Start GRUB4DOS Menu - DOS FPY IMAGES + Linux + XP Rec Cons + Vista"
C:\btsec\XATSP.bs="Attended Setup XP, Never unplug USB-Drive Until After Logon"
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="USB Repair NOT to Start 2. and 3. Continue with GUI Mode Setup Windows XP + Start XP from HD 1" /FASTDETECT
E:\wubildr.mbr = "Ubuntu"

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
# kopt=root=UUID=083c1e3b-16ee-4c0c-89e9-abb281288fdf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=083c1e3b-16ee-4c0c-89e9-abb281288fdf

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        083c1e3b-16ee-4c0c-89e9-abb281288fdf
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=083c1e3b-16ee-4c0c-89e9-abb281288fdf ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        083c1e3b-16ee-4c0c-89e9-abb281288fdf
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=083c1e3b-16ee-4c0c-89e9-abb281288fdf ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        083c1e3b-16ee-4c0c-89e9-abb281288fdf
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows NT/2000/XP (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


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
UUID=083c1e3b-16ee-4c0c-89e9-abb281288fdf /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=cf60af86-e459-474f-a865-8c0150546c81 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 141.8GB: boot/grub/menu.lst
 141.8GB: boot/grub/stage2
 143.4GB: boot/initrd.img-2.6.28-11-generic
 141.8GB: boot/vmlinuz-2.6.28-11-generic
 143.4GB: initrd.img
 141.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 


---

### Post by prodigy_ on 2010-04-15
Ahh, you installed via Wubi. Sorry, I'm not very familiar with it and I can only suggest a clean installation w/o Wubi.

Perhaps someone else can help you better.

---

### Post by dazzyuk on 2010-04-15
No it's not installed via wubi, I uninstalled wubi and installed the full version, it worked fine untill I messed with the partition so just note that wubi did not cause this error it was me creating a new ext3 parition thinking I could use it to reisze my existing install.

---

### Post by prodigy_ on 2010-04-15
In this case I'd say that boot configuration looks alright. Something may be wrong with your Linux partition. Have you tried to check it with fsck?

---

### Post by m4tic on 2010-04-15
> **dazzyuk said:**
> There are loads of threads on this but each one seems to say something different and I do not know which one I should try as I do not want to damage my system any further. 
 
I created a new ext3 partition in Windows and then after a reboot I got an error 17 with grub, I have since deleted that with Gparted from the live USB and resized my drive so Ubuntu has more space, can anyone suggest a way to fix this?
 
I have the following in Gparted:
 
/dev/sda1 - NTFS
 
/dev/sda2 - extended
/dev/sda6 - ext3
/dev/sda7 - linux-swap
/dev/sda5 - linux-swap
 
try this [http://ubuntuforums.org/showpost.php?p=9125385&postcount=10](http://ubuntuforums.org/showpost.php?p=9125385&postcount=10)

---

