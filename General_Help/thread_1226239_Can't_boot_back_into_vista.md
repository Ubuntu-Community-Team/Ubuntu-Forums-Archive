---
title: "Can't boot back into vista??"
date: 2009-07-29
forum: General Help
---

### Post by dq246 on 2009-07-29
HI
I'm a noob, bear with me. The other day i thought it would be cool to install ubuntu linux on my vista computer. I partitioned the hard drive and booted from the linux dvd i had. I followed the on screen instructions to install ubuntu. Im almost positive that the vista partition is there but i just don't know how to boot into it. As soon as my computer turns on it goes straight to ubuntu.  I tried to change the bios and the only thing i could change under boot was the hardrive and not specific partitions. How do i go back to vista?

---

### Post by michy99 on 2009-07-29
Run these commands in a terminal and post the output here.```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by MichealH on 2009-07-29
Well, I am dual booting ubuntu 9.04 and Vista and all works fine (Or have you deleted your vista) Come on we all make mistakes ](*,)

---

### Post by dq246 on 2009-07-29
1.
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

2.
devin@devin-desktop:~$ cat /boot/grub/menu.1st
cat: /boot/grub/menu.1st: No such file or directory

here you go

---

### Post by michy99 on 2009-07-29
In both cases, it is a small l as in lion, not the number 1. Try copy and paste.```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by stlsaint on 2009-07-29
well from initail reading with no further digging...sounds like you overwritten your vista partition! grub loads itself without taking away from!! but thats my dual booting experience..maybe different from yours!

---

### Post by dq246 on 2009-07-29
1
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59719   479692836   83  Linux
/dev/sda2           59720       60801     8691165    5  Extended
/dev/sda5           59720       60801     8691133+  82  Linux swap / Solaris

Disk /dev/sdc: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         488     3919841    b  W95 FAT32

this is the first one the second is super long 
2
[SIZE=1]devin@devin-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=5ce3c8b3-de40-4d63-9383-e2cf30604a8f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ce3c8b3-de40-4d63-9383-e2cf30604a8f

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        5ce3c8b3-de40-4d63-9383-e2cf30604a8f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5ce3c8b3-de40-4d63-9383-e2cf30604a8f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        5ce3c8b3-de40-4d63-9383-e2cf30604a8f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5ce3c8b3-de40-4d63-9383-e2cf30604a8f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        5ce3c8b3-de40-4d63-9383-e2cf30604a8f
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
[/SIZE]

---

### Post by michy99 on 2009-07-29
I am sorry to tell you this, but it looks like you chose 'Use entire disk' when you installed Ubuntu. I don't see a Vista partition anywhere.

---

### Post by dq246 on 2009-07-29
darn o well

---

