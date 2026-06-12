---
title: "Install 7 then grun, now no 7?"
date: 2009-12-22
forum: General Help
---

### Post by running_rabbit07 on 2009-12-22
I installed Windows 7, then I loaded the LiveCD and set up grub. When I restarted, there was no choice to boot Windows. ```
rabbit@rabbit-desktop:~$ [COLOR=Red]sudo cat /boot/grub/menu.lst[/COLOR]
[sudo] password for rabbit: 
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=7d08f642-e45b-4058-b134-f1a6b5702ebb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=7d08f642-e45b-4058-b134-f1a6b5702ebb

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
# defoptions=quiet splash vga=775

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

title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        7d08f642-e45b-4058-b134-f1a6b5702ebb
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=7d08f642-e45b-4058-b134-f1a6b5702ebb ro quiet splash vga=775 
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        7d08f642-e45b-4058-b134-f1a6b5702ebb
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=7d08f642-e45b-4058-b134-f1a6b5702ebb ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic
uuid        7d08f642-e45b-4058-b134-f1a6b5702ebb
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=7d08f642-e45b-4058-b134-f1a6b5702ebb ro quiet splash vga=775 
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
uuid        7d08f642-e45b-4058-b134-f1a6b5702ebb
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=7d08f642-e45b-4058-b134-f1a6b5702ebb ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        7d08f642-e45b-4058-b134-f1a6b5702ebb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7d08f642-e45b-4058-b134-f1a6b5702ebb ro quiet splash vga=775 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        7d08f642-e45b-4058-b134-f1a6b5702ebb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7d08f642-e45b-4058-b134-f1a6b5702ebb ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        7d08f642-e45b-4058-b134-f1a6b5702ebb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

``` ```
rabbit@rabbit-desktop:~$ [COLOR=Red]sudo fdisk -l[/COLOR]

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0defc2af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14444   116021398+   7  HPFS/NTFS
/dev/sda2           14445       16994    20482875   83  Linux
/dev/sda3           16995       30401   107691727+   5  Extended
/dev/sda5           17110       30096   104318077+  83  Linux
/dev/sda6           30098       30401     2441880   82  Linux swap / Solaris
rabbit@rabbit-desktop:~$ 

``` What do I have to do to get Windows back on the list?

Thanks for any and all help.

---

### Post by MooPi on 2009-12-22
I've alway been under the impression that it was always best to have Windows on first, then install Linux (Ubuntu). ?
Well you could fire up gparted and mark your linux partition bootable.
You'll have to excuse me but I can't seem to get anything right to night. PLease proceed.

---

### Post by running_rabbit07 on 2009-12-22
> **MooPi said:**
> I've alway been under the impression that it was always best to have Windows on first, then install Linux (Ubuntu). ?

Windows was working fine until I reinstalled grub.

---

### Post by oldfred on 2009-12-22
menu.lst is grub legacy. and you have NTFS on sda1 so add this after :

Your Win7 entry should be like this:

after this entry you have:
### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows 7 Ultimate, chainloader (on /dev/sda1)
rootnoverify (hd0,0)
savedefault
chainloader +1


Note: boot flag is only used by windows not by ubuntu.

---

### Post by running_rabbit07 on 2009-12-22
> **oldfred said:**
> menu.lst is grub legacy. and you have NTFS on sda1 so add this after :
 
Your Win7 entry should be like this:
 
after this entry you have:
### END DEBIAN AUTOMAGIC KERNELS LIST
 
title Windows 7 Ultimate, chainloader (on /dev/sda1)
rootnoverify (hd0,0)
savedefault
chainloader +1
 
 
Note: boot flag is only used by windows not by ubuntu.
 
That fixed it. Thanks.:)

---

