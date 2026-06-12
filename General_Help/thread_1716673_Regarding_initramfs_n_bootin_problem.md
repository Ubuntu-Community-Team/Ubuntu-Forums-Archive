---
title: "Regarding initramfs n bootin problem"
date: 2011-03-28
forum: General Help
---

### Post by got_in_trouble on 2011-03-28
Hi Everyone ,

I just registered into this forum ,

The thing is that i had ubuntu 8.04 installed with windows vista and it was working perfectly fine since 5-6 months 
yesterday i was working on a final semester project implementing some protocols in ns2 n plotting graphs etc ,and was also installing some packages later i completed my work n properly shut down

Today i cant boot into Ubuntu it is dropping me into initframs again n again

i was able to boot into windows though so i googled tried some trickes like
replacing "quiet splash " with debug or all_generic_ide etc but all in vain

Using some commands i figured out the error actually was 


"[B].... mount : Mounting /dev/disk/by-uuid/9ccof45dcof43f58 on /root failed:

mount : Mounting /root on /host failed : Invalid Argument

ALERT! /host/ubuntu/disks/root.disk  does not exist . Dropping to a shell . "[/B]  


After reading this i logged into windows n found the root.disk file at its place in the partition i did to install Ubuntu .


I had Ubuntu 8.04 CD so i booted into Live (demo) mode downloaded boot info script file and here is the output  

```


    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b35685b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   194,684,927   194,684,865   7 HPFS/NTFS
/dev/sda2         194,684,928   297,084,927   102,400,000   7 HPFS/NTFS
/dev/sda3         297,084,928   312,571,903    15,486,976   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       00127100-6c8b-4609-8cc4-5446c0c85821   ext3                                     
/dev/sda1        3602A70102A6C4E9                       ntfs                                     
/dev/sda2        9CC0F45DC0F43F58                       ntfs       New Volume                    
/dev/sda3        827CA9C47CA9B2F9                       ntfs       PRESARIO_RP                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /media/disk              fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

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
# kopt=root=UUID=9CC0F45DC0F43F58 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=9CC0F45DC0F43F58 loop=/ubuntu/disks/root.disk ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=9CC0F45DC0F43F58 loop=/ubuntu/disks/root.disk ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
chainloader    +1


======================== sda2/ubuntu/winboot/menu.lst: ========================

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

=================== sda2: Location of files loaded by Grub: ===================


 104.3GB: ubuntu/disks/boot/grub/menu.lst
 104.1GB: ubuntu/disks/boot/initrd.img-2.6.24-19-generic
 104.4GB: ubuntu/disks/boot/initrd.img-2.6.24-19-generic.bak
 104.1GB: ubuntu/disks/boot/vmlinuz-2.6.24-19-generic 

```
I really need to boot into Ubuntu all my project files reside there n i have submission coming up this weekend  so plz help me . Thnx in advance

---

### Post by got_in_trouble on 2011-04-04
NO one to Reply ?:(

---

### Post by bcbc on 2011-04-04
The cause can be 1) ntfs corruption, 2) root.disk (ext3) corruption or something else, but since bootinfoscript couldn't mount the ext3 I'd suspect 2).

First thing to do is to insure against catastrophe. Copy the root.disk to a backup.
Second, you could use a tool such as [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) to get readonly access to the root.disk and copy data off it that you don't already have backups for.

Then, run chkdsk /r on the drive that contains the \ubuntu directory. (easiest from My computer, right click on drive, Properties, Tools, Check disk for errors, fix automatically)
Then, boot a live CD and run fsck on the root.disk:
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```

---

