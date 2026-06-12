---
title: "Dualbooting problems with Jaunty and XP"
date: 2009-07-17
forum: General Help
---

### Post by KillerKael on 2009-07-17
Hi. My problem is this: After going through the steps to reduce the partition size for Windows XP and creating a new partition for Linux, installing Linux 9.04, and running Linux, I've run into a problem booting up XP. The first time I tried booting up in Windows XP it went through some sort of system scan to check for continuity of the drives (or something like that) then rebooted my computer once again. Now, whenever I try to boot up XP it just sits there at the "Now loading..." screen. Also, the one time I let it go to try and see if it was just taking a really really long time, it seemed to have either rebooted or booted straight into Linux, but in 800 x 600 resolution. I'm an absolute beginning when it comes to Linux, so any help you can give might have to be given totally step by step because I'll admit it, I'm a noob. Thanks in advance for any help you can give.

---

### Post by TeoBigusGeekus on 2009-07-17
Boot up in Ubuntu and post us the contents of your menu.lst file (that's LST)
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by KillerKael on 2009-07-17
Alrighty....not sure if this is what you need, seems awfully long to me, but here ya go....

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
# kopt=root=UUID=60a4162a-0b33-4a1a-9ddd-3f02a2e63f27 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=60a4162a-0b33-4a1a-9ddd-3f02a2e63f27

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
uuid        60a4162a-0b33-4a1a-9ddd-3f02a2e63f27
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=60a4162a-0b33-4a1a-9ddd-3f02a2e63f27 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        60a4162a-0b33-4a1a-9ddd-3f02a2e63f27
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=60a4162a-0b33-4a1a-9ddd-3f02a2e63f27 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        60a4162a-0b33-4a1a-9ddd-3f02a2e63f27
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60a4162a-0b33-4a1a-9ddd-3f02a2e63f27 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        60a4162a-0b33-4a1a-9ddd-3f02a2e63f27
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=60a4162a-0b33-4a1a-9ddd-3f02a2e63f27 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        60a4162a-0b33-4a1a-9ddd-3f02a2e63f27
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```

---

### Post by merlinus on 2009-07-17
Also post results of:

```
sudo fdisk -l
```

---

### Post by KillerKael on 2009-07-17
Kay....

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60826082

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        2730      955867+  83  Linux
/dev/sda3            2731        9729    56219467+   5  Extended
/dev/sda5            2731        9449    53970336   83  Linux
/dev/sda6            9450        9729     2249068+  82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10248118272 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbe7bbe7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1244     9992398+   7  HPFS/NTFS
```

---

### Post by TeoBigusGeekus on 2009-07-17
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1
```
Try to change this to
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
[COLOR="Red"]root    (hd0,0)[/COLOR]
savedefault
makeactive
chainloader    +1
```
save, reboot and post us what happened.

---

### Post by KillerKael on 2009-07-17
Sorry, it still just sits there at the loading screen for XP.

---

### Post by merlinus on 2009-07-17
You might try supergrub to at least see if you can boot into xp:

[http://supergrubdisk.org](http://supergrubdisk.org)

---

