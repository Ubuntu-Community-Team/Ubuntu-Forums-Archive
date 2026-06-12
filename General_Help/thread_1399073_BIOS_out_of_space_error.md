---
title: "BIOS out of space error"
date: 2010-02-05
forum: General Help
---

### Post by joeknoodle on 2010-02-05
I had several linux-image (kernel?) files, and the latest update now gives me an error to the effect of the image being beyond the BIOS's cylinder count.

So I uninstalled all but one image, and then went back and installed the latest image. Problem is I still get the error.

I'm thinking I need to move the images forward on the HD, but I don't know how, or if that's even what I need to do.

Any help would be appreciated.

---

### Post by warfacegod on 2010-02-05
I may be way off base here but your BIOS isn't stored on the hard drive at all. It should be on the motherboard. Removing kernels and moving things around on the hard drive should have no effect.

---

### Post by joeknoodle on 2010-02-05
My apologies, I should have restarted and got the error for the OP.

I did restart, and here's what I get...

Error 18: selected cylinder exceeds maximum supported by BIOS.

I think this has to do with the boot sector, and having too many images installed before, but I'm not certain.

I still think what I need to do is move those files forward on the HD.

---

### Post by audiomick on 2010-02-05
Hi.
I did a bit of searching. It would seem that you are using
a: an older computer
and
b: grub legacy, i.e. Ubuntu 9.04 or earlier, or a 9.10 that was upgraded and not a fresh install.

If both of these are true, this might help:
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

There is also a reference to "Error 18" in this one
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
in the section "If /boot is in another partition."

---

### Post by ajgreeny on 2010-02-05
Download and run the boot_info_script from here _[http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/)_ and attach the text file it produces back here.  We may be able to help more.

---

### Post by joeknoodle on 2010-02-05
Boot info script:

> 
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4faaccd1

Partition  Boot         Start           End          Size  Id System

/dev/sda1         308,674,800   312,575,759     3,900,960  82 Linux swap / Solaris
/dev/sda2    *             63   308,674,799   308,674,737  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0155d978

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    78,156,224    78,156,162   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   160,826,714   160,826,652  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        40099261-ac0e-4042-84d9-71e49b694a0e   swap                                     
/dev/sda2        89892962-f7ff-442a-b89b-450c737c876e   ext4                                     
/dev/sdb1        7253814F0BD29DBA                       ntfs       JoesSyncer                    
/dev/sdc1        b91dd11f-779e-44ad-ac1a-fc99a240da5b   ext3       Home ext3                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=89892962-f7ff-442a-b89b-450c737c876e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=89892962-f7ff-442a-b89b-450c737c876e

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

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        89892962-f7ff-442a-b89b-450c737c876e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=89892962-f7ff-442a-b89b-450c737c876e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        89892962-f7ff-442a-b89b-450c737c876e
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=89892962-f7ff-442a-b89b-450c737c876e ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-18-generic
uuid        89892962-f7ff-442a-b89b-450c737c876e
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=89892962-f7ff-442a-b89b-450c737c876e ro quiet splash 
initrd        /boot/initrd.img-2.6.31-18-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-18-generic (recovery mode)
uuid        89892962-f7ff-442a-b89b-450c737c876e
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=89892962-f7ff-442a-b89b-450c737c876e ro  single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 9.10, memtest86+
uuid        89892962-f7ff-442a-b89b-450c737c876e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

# Entry for /dev/sda1 :
UUID=40099261-ac0e-4042-84d9-71e49b694a0e swap swap sw 0 0
# Entry for /dev/sda2 :
UUID=89892962-f7ff-442a-b89b-450c737c876e / ext4 defaults 0 1


That's a straight copy/paste, so the emoticons are theirs if that means anything.

---

### Post by audiomick on 2010-02-05
if you use code tags ( the # button) instead of quote, the emoticons don't show up, and it puts a scroll bar in for long blocks.

---

### Post by SecretCode on 2010-02-05
> **joeknoodle said:**
> I think this has to do with the boot sector, and having too many images installed before, but I'm not certain.

It has to do with the latest kernel being placed on your hard drive beyond that BIOS addressing limit. This could have happened with any kernel change.

---

### Post by SecretCode on 2010-02-05
> **audiomick said:**
> Hi.
I did a bit of searching. It would seem that you are using
a: an older computer
and
b: grub legacy, i.e. Ubuntu 9.04 or earlier, or a 9.10 that was upgraded and not a fresh install.

If both of these are true, this might help:
[https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

Wouldn't upgrading to GRUB2 also solve the problem? And be simpler than the /boot partition route?

---

