---
title: "Memory shortage?"
date: 2011-04-28
forum: General Help
---

### Post by Feilin on 2011-04-28
I upgraded to 11.04 and installed some new programs which apparently filled up my memory in my root folder. I reinstalled the system a few days ago, using a 9.04 live-cd, because I wanted a clean system when I try the new release. I understand it might not be the best of things to upgrade from 9.04 to 11.04, but frankly, there aren't many cd's available anymore...

Anywho, following the (old, I s'pose) instructions, I gave the root folder 10 GiB of space, which was too little I realise now, and  my system is on the edge of collapsing (or something; one thing that happened is that my windows lack borders, are immobilised, and the trays at the edges don't even show up, leaving me with my drives only). So I uninstalled some softwares, but I guess it might not've been enough, so is it possible to use gparted from a live-cd to change the partition sizes allowing me to install and update applications like never before without crashing my computer? Or will doing so wreck my system to the point of no recovery?


(OT: Nice look and feel with the 11.04 release btw!)

---

### Post by Hedgehog1 on 2011-04-28
It is indeed possible to use gparted to resize your partitions, but you will have to boot off of a LiveCD/LiveUSB to do that.

If you want some guidance on what should be resized where, please do this:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

p.s. I have starte using 20-30 gigs for '/' (root) partitions and stopped using seperate '/boot' partitions.  It seems to work better.

---

### Post by Feilin on 2011-04-28
Thank you. I think I'll do the same.

To specify my question; will changing the partitions like this disrupt my system, or does gparted take care of any moving of data required? (I recall having messed up my entire system doing something like this in the past...)



Furthermore, now I have an even more interesting problem; namely that right after boot, nothing loads save for my background image, cursor and the drives and folders on my desktop. When I open folders, I have no borders, can't move windows, and the only way to open firefox seems to be through "about" links in nautilus.

Unfortunately I'm not capable of creating a live-USB through terminal, and when I switch session by ctrl + alt + f#, I get the error that it can't load display when I try say "sudo nautilus" (my root folder is locked, only some hundred GiBs left of memory).

What should I do to create a live-USB?





My RESULTS.TXT:

```
 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

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
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sda2          40,965,750   245,762,369   204,796,620   7 HPFS/NTFS
/dev/sda3         245,762,370   625,137,344   379,374,975   5 Extended
/dev/sda5         609,506,100   625,137,344    15,631,245  82 Linux swap / Solaris
/dev/sda6         245,762,496   265,297,409    19,534,914  83 Linux
/dev/sda7         265,297,473   609,490,034   344,192,562  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6468751C6874EDE4                       ntfs                                     
/dev/sda2        1C1F3EFD4F6904C1                       ntfs       Files                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4c223586-8f82-4219-bcef-7366fc64de6a   swap                                     
/dev/sda6        e09c83ab-dc5b-485f-a21b-57e1ecba5265   ext3                                     
/dev/sda7        fc8ca6c7-d5be-46f4-93a6-0a3e2631961c   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro,commit=0)
/dev/sda1        /media/6468751C6874EDE4  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/Files             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7        /home                    ext3       (rw,relatime,commit=0)


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
timeout        3

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
# kopt=root=UUID=e09c83ab-dc5b-485f-a21b-57e1ecba5265 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e09c83ab-dc5b-485f-a21b-57e1ecba5265

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

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
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 11.04, kernel 2.6.38-8-generic
uuid        e09c83ab-dc5b-485f-a21b-57e1ecba5265
kernel        /boot/vmlinuz-2.6.38-8-generic root=UUID=e09c83ab-dc5b-485f-a21b-57e1ecba5265 ro quiet splash 
initrd        /boot/initrd.img-2.6.38-8-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    defaults    0    0
#Entry for /dev/sda6 :
UUID=e09c83ab-dc5b-485f-a21b-57e1ecba5265    /    ext3    relatime,errors=remount-ro    0    1
#Entry for /dev/sda7 :
UUID=fc8ca6c7-d5be-46f4-93a6-0a3e2631961c    /home    ext3    relatime    0    2
#Entry for /dev/sda1 :
UUID=6468751C6874EDE4    /media/6468751C6874EDE4    ntfs-3g    defaults,nosuid,nodev,locale=C    0    0
#Entry for /dev/sda2 :
UUID=1C1F3EFD4F6904C1    /media/Files    ntfs-3g    defaults,nosuid,nodev,locale=C    0    0
#Entry for /dev/sda5 :
UUID=4c223586-8f82-4219-bcef-7366fc64de6a    none    swap    sw    0    0
/dev/scd0    /media/cdrom0    udf,iso9660    user,noauto,exec,utf8    0    0



=================== sda6: Location of files loaded by Grub: ===================


 126.6GB: boot/grub/menu.lst
 126.6GB: boot/grub/stage2
 126.6GB: boot/initrd.img-2.6.28-11-generic
 126.7GB: boot/initrd.img-2.6.31-23-generic
 126.7GB: boot/initrd.img-2.6.35-28-generic
 126.7GB: boot/initrd.img-2.6.38-8-generic
 126.6GB: boot/vmlinuz-2.6.28-11-generic
 126.6GB: boot/vmlinuz-2.6.31-23-generic
 126.7GB: boot/vmlinuz-2.6.35-28-generic
 126.7GB: boot/vmlinuz-2.6.38-8-generic
 126.7GB: initrd.img
 126.7GB: initrd.img.old
 126.7GB: vmlinuz
 126.7GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ls: reading directory /media/Files/: Invalid or incomplete multibyte or wide character
```

---

