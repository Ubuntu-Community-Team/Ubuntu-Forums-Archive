---
title: "Win7 + Ubuntu 9.10 - Error 13: Invalid or unsupported executable format error"
date: 2010-04-24
forum: General Help
---

### Post by Exodus_UK on 2010-04-24
Hello,

I've just did a fresh install of Win7 and Ubuntu respectively, but after installing Ubuntu, it was booting straight into it, and wasnt giving me any chance to even choose wich OS to boot.

Then I added the win7 entry to menu.lst, and when i tried to boot into Win7 it was giving me the topic error.

This is my menu.lst:
>  # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=/dev/mapper/isw_ddgjbgcadi_Volume03 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title        Ubuntu 9.10, kernel 2.6.31-14-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_ddgjbgcadi_Volume03 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_ddgjbgcadi_Volume03 ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin

title windows 7 beta (Loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST And this is the fdisk -l:
> Disk / dev / sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors / track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Identifier of the disc: 0x00000000

Disk / dev / sda does not contain a valid partition table

Disk / dev / sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors / track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Identifier of the disc: 0xddb7653c

Device Boot Start End Blocks Id System
/ Dev/sdb1 1 63 742 512 000 000 7 HPFS or NTFS
/ Dev/sdb2 * 63 743 65 200 11,711,385 82 Linux swap / Solaris
/ Dev/sdb3 65201 68847 29294527 + 83 Linux
/ Dev/sdb4 68 848 121 602 423 754 537 + 83 LinuxHave u guys any advice for me?

I think i gave enough info, but should you need any other info please ask me!

Thank you!

PS.: I did searched through the forum, but no success as there was many different scenarios.

---

### Post by wilee-nilee on 2010-04-25
Post this boot script with code tags it will give the information needed.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Exodus_UK on 2010-05-01
Sry for the late response, this problem is solved now, I've just decided to move on and forget windows forever, so I did a fresh installation of Ubuntu and deleted windows of my life...

thx!!

---

