---
title: "GRUB cannot find Windows (bizarre)"
date: 2010-09-09
forum: General Help
---

### Post by efosmark on 2010-09-09
**Current set-up:**
Ubuntu 9.04 and Windows XP partitioned on one single hard-drive.
There is a small other partition (Fat32) that I used for storing files on.

Let me explain what happened. I put in a Fedora 13 live CD, and then afterwards I got an "NTLDR is missing message" when I tried to boot into Windows. After trying to fix that with fixmbr/fixboot/chkdisk, I just gave up and put grub back in the MBR. After running update-grub it can't see Windows anymore.

The weird thing is, I can access the Windows partition just fine through Ubuntu, but when I generated a new menu.lst file for GRUB, it doesn't show up in the GRUB listing. Obviously there's a problem somewhere.

If I need to provide any information, just ask for it and I will be happy to comply.

Cheers,
Evan

---

### Post by mohansathish on 2010-09-09
The menu entry of your windows Operating system is erased from the MBR and that's the reason why grub is not identifying the correct windows partition. 

You can try configuring the grub with manually making the boot loader to boot the partition where you installed windows. (It might work sometimes and vice versa)

Good Luck

---

### Post by efosmark on 2010-09-09
Here is information from running Boot Info Script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /boot.ini /NTLDR /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xebb7d3f9

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    21,061,214    21,061,152   c W95 FAT32 (LBA)
/dev/sda2          21,061,215   488,279,609   467,218,395   f W95 Ext d (LBA)
/dev/sda5    *     21,062,223   123,454,799   102,392,577   7 HPFS/NTFS
/dev/sda6         123,459,588   136,713,149    13,253,562  82 Linux swap / Solaris
/dev/sda7         136,713,213   488,279,609   351,566,397  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2C74-EB8A                              vfat                                     
/dev/sda5        D4E0D91AE0D903A0                       ntfs                                     
/dev/sda6        7d3ddccf-953b-455a-b8aa-a1b84cbb3bb1   swap                                     
/dev/sda7        5a560197-27d0-426c-9530-68c3640cd3b0   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda5/boot.ini: ================================

[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDEX
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDEX="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda7/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5a560197-27d0-426c-9530-68c3640cd3b0

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

title        Ubuntu 9.04, kernel 2.6.28-19-generic
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-19-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-19-generic (recovery mode)
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-19-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro  single
initrd        /boot/initrd.img-2.6.28-19-generic

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5a560197-27d0-426c-9530-68c3640cd3b0 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5a560197-27d0-426c-9530-68c3640cd3b0
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=5a560197-27d0-426c-9530-68c3640cd3b0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7d3ddccf-953b-455a-b8aa-a1b84cbb3bb1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 218.8GB: boot/grub/menu.lst
 220.4GB: boot/grub/stage2
 218.9GB: boot/initrd.img-2.6.28-11-generic
 218.9GB: boot/initrd.img-2.6.28-13-generic
 218.9GB: boot/initrd.img-2.6.28-14-generic
 203.4GB: boot/initrd.img-2.6.28-15-generic
 227.5GB: boot/initrd.img-2.6.28-19-generic
 218.9GB: boot/vmlinuz-2.6.28-11-generic
 218.9GB: boot/vmlinuz-2.6.28-13-generic
 218.9GB: boot/vmlinuz-2.6.28-14-generic
 170.2GB: boot/vmlinuz-2.6.28-15-generic
 218.9GB: boot/vmlinuz-2.6.28-19-generic
 227.5GB: initrd.img
 203.4GB: initrd.img.old
 218.9GB: vmlinuz
 170.2GB: vmlinuz.old

```

---

### Post by garvinrick4 on 2010-09-09
Can Windows run in a logical partition? I was of the mind that Windows needs a primary to
run in.

---

### Post by Rubi1200 on 2010-09-09
Also, it appears as if you may be missing boot files for Ubuntu on sda7.

---

