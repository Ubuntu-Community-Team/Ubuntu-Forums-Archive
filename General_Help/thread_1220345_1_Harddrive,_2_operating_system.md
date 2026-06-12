---
title: "1 Harddrive, 2 operating system"
date: 2009-07-22
forum: General Help
---

### Post by relaxedcrazyman on 2009-07-22
This is a little bit odd, but just curious if anyone can help me..

HDD1: 160gb Vista Ultimate
HDD2: 1tb storage/Ubuntu 9.04/Windows 7 (just installed)


So whenever i boot up from hdd2 i get the Grub boot menu, and it has the

Ubuntu

Other Operating System:
Windows Vista

but it doesnt boot to vista, and i was wondering if how i can get Windows 7 onto the grub boot menu. is it possible with them being on the same harddrive?

---

### Post by rraj.be on 2009-07-22
It is possible. 

Just add your new entry into the grub . .The only change will be Instead of hd0 you will be using hd1

---

### Post by merlinus on 2009-07-22
Post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by relaxedcrazyman on 2009-07-22
```
themaster@themaster-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff2db8be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3df7ad1d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      117088   940509328+   7  HPFS/NTFS
/dev/sdb2          119129      121601    19864372+   5  Extended
/dev/sdb3          117089      119128    16386300    7  HPFS/NTFS
/dev/sdb5          119130      121041    15358140   83  Linux
/dev/sdb6          121042      121601     4498168+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?         410      119791   958924038+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?      121585      234786   909287957+  43  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?       14052       14052           5   72  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdc4          164483      164486       25945    0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```


i believe sdb3 is the one with windows 7 installed



```
themaster@themaster-desktop:~$ cat /boot/grub/menu.lst
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=37a9510d-b4be-45c4-b9a9-f65ac42675f6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=37a9510d-b4be-45c4-b9a9-f65ac42675f6

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
# defoptions=splash vga=792 quiet

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		37a9510d-b4be-45c4-b9a9-f65ac42675f6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=37a9510d-b4be-45c4-b9a9-f65ac42675f6 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		37a9510d-b4be-45c4-b9a9-f65ac42675f6
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=37a9510d-b4be-45c4-b9a9-f65ac42675f6 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		37a9510d-b4be-45c4-b9a9-f65ac42675f6
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by merlinus on 2009-07-22
If you ae booting from sdb (second hdd), then change the vista stanzas to:

title        Windows Vista (loader)
rootnoverify    (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1

and restart.

---

### Post by relaxedcrazyman on 2009-07-22
> **merlinus said:**
> If you ae booting from sdb (second hdd), then change the vista stanzas to:

title        Windows Vista (loader)
rootnoverify    (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader    +1

and restart.

is that to run vista from the bootloader?


i am booting from the 1 tb drive, guessing sdb, if that gets vista to work as well, that is an awesome plus, but i am trying to add windows 7, guessing sdb3, on the 1tb drive onto the bootloader

---

### Post by merlinus on 2009-07-22
If you are booting from the hdd with linux, then that should boot vista.  For win 7, try adding this, either above or below the one for vista:

title        Windows7
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1

---

### Post by relaxedcrazyman on 2009-07-22
Was odd, but ended up working out...

When i first tried to run Windows 7, i got this:

```
Starting up...
BOOTMGR is missing

Press CTRL+ALT+DEL to restart
```

so i restarted, then tried Vista, it ran fine, and the Windows bootloader came up, and Vista and Windows 7 both worked fine from there.

so, i guess it all works out :)


thanks a million for your quick speedy helpful help.

---

### Post by merlinus on 2009-07-22
Glad it is working.  Have fun, and post back if you run into difficulties.

---

