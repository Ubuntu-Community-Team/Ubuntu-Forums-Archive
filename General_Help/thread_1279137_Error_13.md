---
title: "Error 13"
date: 2009-09-30
forum: General Help
---

### Post by searover on 2009-09-30
Hi,
I've been runing ubuntu on one hard disc and windows on another, i recently had to reinstall 9.04 as it was refusing to make any updates, since that time it worked fine but i needed to run windows the other day and found that when i try to load xp the error 13 comes up, i could try to repair windows but i can still mount the drive and it looks good, i feel that the problem is with the area that gives the option to load other os. any idears.

---

### Post by mac9416 on 2009-09-30
Could you please post your /boot/grub/menu.lst? Thanks.

---

### Post by searover on 2009-09-30
menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=159b1d45-c611-4057-a64e-bd43f3796b4d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=159b1d45-c611-4057-a64e-bd43f3796b4d

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		159b1d45-c611-4057-a64e-bd43f3796b4d
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=159b1d45-c611-4057-a64e-bd43f3796b4d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		159b1d45-c611-4057-a64e-bd43f3796b4d
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=159b1d45-c611-4057-a64e-bd43f3796b4d ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		159b1d45-c611-4057-a64e-bd43f3796b4d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=159b1d45-c611-4057-a64e-bd43f3796b4d ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		159b1d45-c611-4057-a64e-bd43f3796b4d
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=159b1d45-c611-4057-a64e-bd43f3796b4d ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		159b1d45-c611-4057-a64e-bd43f3796b4d
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by mac9416 on 2009-09-30
> title Microsoft Windows XP Home Edition
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

Well, to my untrained eye that part looks fine, assuming XP is on the slave drive. Could you post the output of this command so I can get a better idea of what your drives and filesystems look like?

```
$ sudo fdisk -l
```

Thanks for your patience, I am nowhere near an expert at this, but hopefully we can find the problem. :)

---

### Post by searover on 2009-10-01
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ab30275

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72d872d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25cb4714

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       37457   300873321   83  Linux
/dev/sdc2           37458       38913    11695320    5  Extended
/dev/sdc5           37458       38913    11695288+  82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    c  W95 FAT32 (LBA)
dave@dave-desktop:~$ 
hi the reason i keep things separate is that in the past i had several hard driver fail so my important stuff is kept on different drives to the operating systems, then if i need to reinstall nothing to lose. i think the 9.04 is starting to slide into the place it was when i did the reinstall, its starting not to see some external usb memory sticks, which is how it started last time, it lost some external drives then refused to update. this may be part of the same trouble? 
thanks for the assistance.

---

### Post by mac9416 on 2009-10-01
> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ab30275

Device Boot Start End Blocks Id System
/dev/sda1 * 1 121601 976760001 7 HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72d872d8

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 9728 78140128+ 7 HPFS/NTFS

From that, I can tell that you have two drives with NTFS partitions on them. Either of those could be your XP install. Since your menu.lst is configured to boot from the second disk, and that's not working, let's change it to the first disk and see what that does.

Change

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Home Edition
rootnoverify (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

to

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1 

Then try to boot XP.

Like I say, I'm a bit of a n00b, so I'm crossing my fingers the same as you. I found a very good explanation by Unutbu how this kind of problem could be caused here: [http://ubuntuforums.org/showthread.php?t=1214106&page=2](http://ubuntuforums.org/showthread.php?t=1214106&page=2)

Good luck!

---

### Post by searover on 2009-10-01
hi mac,
thats it sorted, thanks again for your assistance, i did look through the threads but i'm not very good at searches.
best regards....

---

