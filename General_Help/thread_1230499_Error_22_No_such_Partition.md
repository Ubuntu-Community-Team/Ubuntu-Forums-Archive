---
title: "Error 22 No such Partition"
date: 2009-08-03
forum: General Help
---

### Post by Abhishek4563 on 2009-08-03
Hey this is my first post ... so I need to mention its a great forum and I salute all the contributors....

I just installed Jaunty 32-bit and had woking windows on the same drive ..now after installing windows I believe I have atleast once accessed windows ... but then i resarted and windows is showing in the grub menu but when i select it ..it says no such partition ...I plugged in the windows cd and was able to enter the recovery console so that kind of makes sure that I still have windows on the drive ...I started partition editor and it showed a exclamation mark in front of the windows drives(which hould mean its corrupted) but I was able to access it from ubuntu ... now what should I do ??? I really dont want to  reinstall Windows ...could it be bcoz ubuntu locked the access of the drive should i un-mount or if i need to change the menu.lst what changes should  i make ... I even tried super grub disk ..but it doesnt work for me ...

---

### Post by merlinus on 2009-08-03
Post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by tjwoosta on 2009-08-03
please post the outputs of the following commands

```
sudo gedit /boot/grub/menu.lst
```

and 

```
sudo fdisk -l
```

EDIT: lol, merlinus beat me to it

---

### Post by Abhishek4563 on 2009-08-03
```
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
# kopt=root=UUID=5b38a074-6008-4234-807f-c128ee3a6983 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5b38a074-6008-4234-807f-c128ee3a6983

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        5b38a074-6008-4234-807f-c128ee3a6983
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5b38a074-6008-4234-807f-c128ee3a6983 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        5b38a074-6008-4234-807f-c128ee3a6983
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=5b38a074-6008-4234-807f-c128ee3a6983 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5b38a074-6008-4234-807f-c128ee3a6983
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5b38a074-6008-4234-807f-c128ee3a6983 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5b38a074-6008-4234-807f-c128ee3a6983
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5b38a074-6008-4234-807f-c128ee3a6983 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5b38a074-6008-4234-807f-c128ee3a6983
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title        Windows NT/2000/XP (loader)
rootnoverify    (hd1,2)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```and

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x25b625b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    7  HPFS/NTFS
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d642d64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+   5  Extended
/dev/sdb2            2577       19457   135596632+   7  HPFS/NTFS
/dev/sdb3            1302        2576    10241437+   7  HPFS/NTFS
/dev/sdb4   *         123        1301     9470317+  83  Linux
/dev/sdb5               1         122      979902   82  Linux swap / Solaris

Partition table entries are not in disk order

```These are the outputs

I believe sdb3 has windows since one of the NTFS is 9gb other one 129 GB and windows is on 9GB one

---

### Post by merlinus on 2009-08-03
What is the boot order of your hdds in bios?

Also, you have a boot flag set on sda4, which is listed as an empty partition, and none on sdb3, which seems to be windows.

You can change these using gparted.

Linux does not need boot flags.

---

### Post by Abhishek4563 on 2009-08-03
I edited my ealier post sdb3 has windows sda has only data ...so is there any option to set boot flags in gparted I am going to try that right away ... about boot order I only knwo that it checks DVD drive then disks ..since till now there was no problem with external disk i never checked it . i guess i ll enter BIOS and post the boot order ??? i.e hd0 then hd1  or hd1 then hd0...

---

### Post by tjwoosta on 2009-08-03
this is just a guess, but try commenting out these lines and see what happens

# map        (hd0) (hd1)
# map        (hd1) (hd0)

# title        Other operating systems:
# root


EDIT: nvm, sry I see now that those are probably required because your booting from a second hd

---

### Post by merlinus on 2009-08-03
According to the entries in menu.lst, the hdd windows is on needs to be second in hdd boot order.

---

### Post by Abhishek4563 on 2009-08-03
thank you guys .. I just changed the hdd boot sequence and it worked like charm ... though this is not the end of my problems ... I still have my graphics card not working and have to configure two monitors but I guess I will start a nes thread inan appropriate place with appropriate serching before posting ...thx again

---

### Post by ibuclaw on 2009-08-03
> **Abhishek4563 said:**
> thank you guys .. I just changed the hdd boot sequence and it worked like charm ... though this is not the end of my problems ... I still have my graphics card not working and have to configure two monitors but I guess I will start a nes thread inan appropriate place with appropriate serching before posting ...thx again

You have two graphics cards?

If so, I advise you to start a new thread with the output from the following commands:
```
lspci
```
```
cat /etc/X11/xorg.conf
```
And I'll post what you need to do to get your dual-monitors setup. :)

Regards
Iain

---

