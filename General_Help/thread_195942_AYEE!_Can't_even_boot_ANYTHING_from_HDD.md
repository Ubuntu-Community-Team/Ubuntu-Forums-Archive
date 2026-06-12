---
title: "AYEE! Can't even boot ANYTHING from HDD"
date: 2006-06-13
forum: General Help
---

### Post by Stormx on 2006-06-13
Oh bummer! I just installed Windows XP and I thought it would be pretty easy to reinstall grub... apparently not. Heres my setup

hda1 = Windows XP
hda2 = Windows 2000
hdb1 = FAT Parition
hdb2 = Ubuntu
hdb something = Ubuntu SWAP

When I boot up my computer, it tries my floppy disk drive and CD ROM drives, then just hangs. Its started doing this after I tried to reinstall grub from the ubuntu live cd, I tried Super GRUB CD before that. I've tried basicly everything on the wiki page, and I have no idea what to do! I'm working off Live CDs at the moment which is a tad fustrating. Please, any ideas? I don't have a /boot partition.....

Damn, I forgot it changed! More info:

ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS
/dev/hda2            2434        4864    19527007+   f  W95 Ext'd (LBA)
/dev/hda5            2434        4864    19526976    7  HPFS/NTFS


--------------------menu.list-------------------------
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.15-22-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-22-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-22-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-22-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-22-386
boot

title		Ubuntu, kernel 2.6.15-21-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-21-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-21-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.15-21-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.15-21-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---------------------------fstab of ubuntu parition---------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults,user_xattr        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


#Added by diskmounter utility
/dev/hda5 /media/Win2K ntfs ro,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/hda1 /media/Win98 vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
#Added by diskmounter utility
/dev/hdb1 /media/Media vfat rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0

---

### Post by noswal on 2006-06-13
Check you bios setup that it can boot from a hard disk.

This is what I did, though I had access to XP
[http://www.ubuntuforums.org/showthread.php?t=193624](http://www.ubuntuforums.org/showthread.php?t=193624)

---

### Post by Stormx on 2006-06-13
Well i guess it was booting from a hard disk right? I'll have a check....

---

### Post by zxee on 2006-06-13
From the live cd do sudo chroot /dev/hda2  then, grub <enter>
at the grub prompt (grub >) do find /boot/grub/stage1 that command should just find your ubuntu partition and output it in grub notation (hd1,1)
If that's the case then do setup (hd1,1) which will write grub to your root partition not the MBR. If you want it on your MBR then just setup (hd0) but then you won't be able to boot windows without editing grub. Hope that helps.

---

### Post by Stormx on 2006-06-13
chroot: cannot change root directory to /dev/hda2: Not a directory

---

### Post by zxee on 2006-06-13
[QUOTE=Stormx]chroot: cannot change root directory to /dev/hda2: Not a directory[/QUOTE]
Sorry that was my error (typo) try sudo chroot /dev/hdb2

---

### Post by noswal on 2006-06-13
At the bottom of your first post it only has a Grub access to Win2000 on hda1 though at the top of that post it says hda1 is XP

I used this as once I got back into ubuntu it would not see my hda1

[https://wiki.ubuntu.com/MountNtfsOnBoot](https://wiki.ubuntu.com/MountNtfsOnBoot)

---

### Post by Stormx on 2006-06-13
I really don't know.... I think I'm just gonna reinstall dapper... gonna give it an hour or so, just to see if anyone has any other ideas...

---

### Post by noswal on 2006-06-13
so add this change into the bottom of your menu.lst and reboot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP
root (hd0,0)
savedefault
makeactive
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Microsoft Windows 2000 Professional
root (hd0,1)
savedefault
makeactive
chainloader +1

---

### Post by zxee on 2006-06-13
[QUOTE=zxee]Sorry that was my error (typo) try sudo chroot /dev/hdb2[/QUOTE]

Did you notice that I corrected my typo? This should work but re-installing is fun too.

---

### Post by Stormx on 2006-06-13
It wasn't a menu.list problem. GRUB never loaded in the first place. Anyway I've reinstalled dapper now, so never mind!

---

