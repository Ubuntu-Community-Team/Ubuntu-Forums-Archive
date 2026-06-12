---
title: "Error 21.."
date: 2010-12-22
forum: General Help
---

### Post by lil_kid1333 on 2010-12-22
Well I've been getting the dreaded error 21 from grub.. Here's the story:

My win xp was lagging on me so I decided to reinstall it, but I also made it larger using Gparted. I loaded up this win xp cd I have but the problem was it's scratched so it didn't install correctly. Then I tried the original win xp cd and for some reason even with the unpartitioned space, it WONT let me install O.o! Keeps saying unknown disk. And well I can't use the other win xp cd cause it's scratched and will install all corruped.

I used Gparted to make the unpartitioned space into NTFS and it makes it but the original cd still won't let me install. I used the original xp cd on a different HDD and it loads up there and installs fine.

So I decided to re-install grub using the grub (hd0) commands so I could at least use ubuntu for now but I keep getting the error 21.. any help appreciated. I'm using ubuntu 8.10 btw..

---

### Post by karthick87 on 2010-12-22
Post the results of [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) with code(#) tags.

---

### Post by lil_kid1333 on 2010-12-22
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe2c8e2c8

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   167,170,047   167,169,985  83 Linux
/dev/sda3         309,572,550   312,576,704     3,004,155   5 Extended
/dev/sda5         309,572,613   312,576,704     3,004,092  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c95d1f16-a008-47a3-929b-a52438473996   ext3                                     
/dev/sda5        187365c8-8fa5-457b-a0b8-fede961ea0ce   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
# kopt=root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa

## default grub root device
## e.g. groot=(hd0,0)
# groot=c95d1f16-a008-47a3-929b-a52438473996

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

title		Ubuntu 8.10, kernel 2.6.27-17-generic
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-17-generic (recovery mode)
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-17-generic

title		Ubuntu 8.10, kernel 2.6.27-16-generic
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-16-generic

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c95d1f16-a008-47a3-929b-a52438473996 ro xforcevesa  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c95d1f16-a008-47a3-929b-a52438473996
kernel		/boot/memtest86+.bin
quiet

title Microsoft Winblows
root (hd0,1)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c95d1f16-a008-47a3-929b-a52438473996 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=187365c8-8fa5-457b-a0b8-fede961ea0ce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  58.2GB: boot/grub/menu.lst
  58.2GB: boot/grub/stage2
  58.3GB: boot/initrd.img-2.6.27-11-generic
  75.5GB: boot/initrd.img-2.6.27-14-generic
  58.4GB: boot/initrd.img-2.6.27-16-generic
  69.0GB: boot/initrd.img-2.6.27-17-generic
  58.2GB: boot/initrd.img-2.6.27-7-generic
   2.6GB: boot/vmlinuz-2.6.27-11-generic
  19.5GB: boot/vmlinuz-2.6.27-14-generic
  58.3GB: boot/vmlinuz-2.6.27-16-generic
  71.4GB: boot/vmlinuz-2.6.27-17-generic
  58.3GB: boot/vmlinuz-2.6.27-7-generic
  69.0GB: initrd.img
  58.4GB: initrd.img.old
  71.4GB: vmlinuz
  58.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by psusi on 2010-12-22
8.10 is obsolete and no longer supported; you should upgrade immediately.  I'd suggest just doing a clean install of 10.04 or 10.10 ( if you don't want to stick to LTS ).

---

### Post by lil_kid1333 on 2010-12-22
ok well I'll do that but I want to back up my memory lol so can anyone help me with that error21?

---

### Post by oldfred on 2010-12-22
You need to reinstall grub legacy. You should be able to use a liveCD to boot and then copy all your files.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

from liveCD
#reset grub boot
sudo grub
find /boot/grub/stage1 #you will get a response such as  (hd0,0)
root (hd0,0) #use the numbers from the previous command x is drive, y is partition  or root (hd0,5)
setup (hd0)
quit

---

### Post by psusi on 2010-12-23
If you install 10.04 or 10.10, use manual partitioning, configure your partitions, and do NOT check the format box, and everything in your /home directory will remain intact.

---

