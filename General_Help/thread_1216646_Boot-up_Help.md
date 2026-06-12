---
title: "Boot-up Help"
date: 2009-07-18
forum: General Help
---

### Post by Khrimzunn on 2009-07-18
Ok, well recently I bought a new fan, added it in, wired it up, got a new HDD, wired it up, installed Vista AFTER Ubuntu. (Stupid, yes I know.) 
Ok, so I tried to make grub recognize my other HDD, and give me a boot option to it. But I couldn't get it to work. 

So, how can I make my computer reinstall grub, and tell it to use the other HDD as a bootable HDD. So I can boot into either Ubuntu, or Vista trough grub, not going trough bios?

Any halp is much appreciated. Thanks. :3

---

### Post by merlinus on 2009-07-18
Post results of

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by Khrimzunn on 2009-07-18
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000472ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384512    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d445d44

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       59672   479315308+  83  Linux
/dev/sdb2           59673       60801     9068692+   5  Extended
/dev/sdb5           59673       60801     9068661   82  Linux swap / Solaris




:~$ cat /boot/grub/menu.lst
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
#      password --md5 (Hidden by me)/
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
# kopt=root=UUID=ae654231-9cc6-4c41-966c-5e08544f7cee ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=ae654231-9cc6-4c41-966c-5e08544f7cee

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
uuid        ae654231-9cc6-4c41-966c-5e08544f7cee
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ae654231-9cc6-4c41-966c-5e08544f7cee ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        ae654231-9cc6-4c41-966c-5e08544f7cee
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ae654231-9cc6-4c41-966c-5e08544f7cee ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ae654231-9cc6-4c41-966c-5e08544f7cee
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae654231-9cc6-4c41-966c-5e08544f7cee ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ae654231-9cc6-4c41-966c-5e08544f7cee
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ae654231-9cc6-4c41-966c-5e08544f7cee ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ae654231-9cc6-4c41-966c-5e08544f7cee
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=515bf795-f436-40f1-95ba-7192b31476c1 ro splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=515bf795-f436-40f1-95ba-7192b31476c1 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, memtest86+ (on /dev/sda2)
root        (hd0,1)
kernel        /boot/memtest86+.bin  
savedefault
boot

```

---

### Post by merlinus on 2009-07-18
First of all, these stanzas refer to your previous installation, so you can comment them out by placing a hashmark (#) in front of the lines that do not already have them -- or you can delete them entirely.


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=515bf795-f436-40f1-95ba-7192b31476c1 ro splash 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=515bf795-f436-40f1-95ba-7192b31476c1 ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        Ubuntu 9.04, memtest86+ (on /dev/sda2)
root        (hd0,1)
kernel        /boot/memtest86+.bin  
savedefault
boot

Then add this to the end of the file:

title Vista
rootnoverify (hd0,0)
makeactive
chainloader +1

Restart and see what happens.

---

### Post by Khrimzunn on 2009-07-18
Oh cool. Thanks a lot. 
I was worried about editing that file since I messed it up the first time I edited it.

---

