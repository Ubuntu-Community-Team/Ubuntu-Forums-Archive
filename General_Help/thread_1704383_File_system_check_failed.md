---
title: "File system check failed"
date: 2011-03-10
forum: General Help
---

### Post by raultejada on 2011-03-10
Hello Ubuntu Forum Community, this is my first thread post so please understand what Im saying.

I have a Hp Netbook, and my friend installed Ubuntu to my computer. Everything was going fine, until one day my battery died while I was searching the web. I turned it back on and It started checking files and then it took me to a black screen with white letters saying "File System check failed", im not that good with computers so I need someone to help me fast. I went to this other forum that told me to input a command "fsck" and it just gave me a error. Please help me ASAP. Id appericate it :)

---

### Post by Rubi1200 on 2011-03-10
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Hedgehog1 on 2011-03-10
> **raultejada said:**
> 
I have a Hp Netbook, and my friend installed Ubuntu to my computer. Everything was going fine, until one day my battery died while I was searching the web. I turned it back on and It started checking files and then it took me to a black screen with white letters saying "File System check failed"

[SIZE="3"]**EDIT: Please run the script Rubi1200 asked you to do first.**[/SIZE]

raultejada,

Losing power when writing to disk can cause issues with any OS.   *It is never fun.*

The first step is to boot boot from an Ubuntu LiveCD or a Bootable USB stick with the 'LiveCD' on it. Many netbooks have no CD drive, so booting from USB stick for repairs is our only option. Here is a link to show you how to make onef you don't have a USB stick to boot from yet: [http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/]("http://www.pendrivelinux.com/creating-an-ubuntu-live-usb-from-cd/")

Once you boot from a CD or USB stick, pick the try option. Then you can run gparted, lighlight your partiton, right click on it and select 'check'.

Also, here is a link about fsck: [http://linux.die.net/man/8/fsck]("http://linux.die.net/man/8/fsck")

These are the basic tools.  Other will likely have addition options for you.

***The Hedge***

:KS

---

### Post by Flying Karapet on 2011-03-15
Hello Iam his friend the guy who had first installed ubuntu on his netbook I did as you said Rubi1200 Thanks. Here are the results 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ae9b4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   150,336,269   150,336,207  83 Linux
/dev/sda2         150,336,270   156,296,384     5,960,115   5 Extended
/dev/sda5         150,336,333   156,296,384     5,960,052  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2031 MB, 2031091712 bytes
16 heads, 32 sectors/track, 7748 cylinders, total 3966976 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009bbfc

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     3,966,975     3,958,912   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 3963 MB, 3963617280 bytes
128 heads, 63 sectors/track, 960 cylinders, total 7741440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               8,192     7,741,439     7,733,248   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       739f15d4-abf3-4b93-989a-ae194513e231   ext3                                     
/dev/sda1        b3d515e9-53c4-4098-9051-bf8eee48fece   ext3                                     
/dev/sda5        5c5682de-c1a3-46de-897f-eddc0a6bebaf   swap                                     
/dev/sdb1        52B3-6751                              vfat       2 GB M                        
/dev/sdc1        0ABC-5E8A                              vfat       4 GB K                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sdb1        /cdrom                   vfat       (rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/4 GB  K           vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=b3d515e9-53c4-4098-9051-bf8eee48fece ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=b3d515e9-53c4-4098-9051-bf8eee48fece

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

title		Ubuntu 9.10, kernel 2.6.31-22-generic
uuid		b3d515e9-53c4-4098-9051-bf8eee48fece
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=b3d515e9-53c4-4098-9051-bf8eee48fece ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-22-generic (recovery mode)
uuid		b3d515e9-53c4-4098-9051-bf8eee48fece
kernel		/boot/vmlinuz-2.6.31-22-generic root=UUID=b3d515e9-53c4-4098-9051-bf8eee48fece ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 9.10, kernel 2.6.28-19-generic
uuid		b3d515e9-53c4-4098-9051-bf8eee48fece
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=b3d515e9-53c4-4098-9051-bf8eee48fece ro quiet splash 
initrd		/boot/initrd.img-2.6.28-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-19-generic (recovery mode)
uuid		b3d515e9-53c4-4098-9051-bf8eee48fece
kernel		/boot/vmlinuz-2.6.28-19-generic root=UUID=b3d515e9-53c4-4098-9051-bf8eee48fece ro  single
initrd		/boot/initrd.img-2.6.28-19-generic

title		Ubuntu 9.10, memtest86+
uuid		b3d515e9-53c4-4098-9051-bf8eee48fece
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b3d515e9-53c4-4098-9051-bf8eee48fece /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5c5682de-c1a3-46de-897f-eddc0a6bebaf none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   7.3GB: boot/grub/menu.lst
   7.2GB: boot/grub/stage2
   7.3GB: boot/initrd.img-2.6.28-19-generic
   7.2GB: boot/initrd.img-2.6.31-22-generic
   7.2GB: boot/vmlinuz-2.6.28-19-generic
   7.2GB: boot/vmlinuz-2.6.31-22-generic
   7.2GB: initrd.img
   7.3GB: initrd.img.old
   7.2GB: vmlinuz
   7.2GB: vmlinuz.old

```

I was wondering wouldn't it be easier if I just reinstall 
Ubuntu 9.04

---

