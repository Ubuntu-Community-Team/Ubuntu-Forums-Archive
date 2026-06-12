---
title: "Help with boot partitioning"
date: 2009-09-28
forum: General Help
---

### Post by Joshka89 on 2009-09-28
Ok. So right now I have Ubuntu on one partition, there is no separate boot partition for GRUB at all.

I have 110GB HDD and have split it directly in half so I can dual boot it.

What I want to do is make a 100MB partition to move GRUB boot info onto.

Next I will install Windows 7 on the unallocated space. When I install W7 it will also create a 100MB partition for booting.

With this setup I will have as follows:

100MB GRUB Boot
55GB Ubuntu
100MB W7 Boot
54.9GB Windows 7

How do I do this properly? I dont know how to move my Ubuntu boot info to the new 100MB partition I have just created and I cant seem to find a How To on it anywhere.


My reasoning for doing this is that I has previously installed W7 on the free 55GB of space, but its boot ate my GRUB boot so I followed [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999) tutorial on fixing this problem

What happened then was that I overwrote my W7 boot partition so I could not properly boot it.

With this way I want to partition it, I can edit my /boot/grub/menu.lst to do all GRUB booting from the 100MB GBoot partition, and then all windows booting from the 100MB W7 partition.

So far I have attempted to do sudo grub-install --root-directory=/media/root /dev/sda2
sda2 is my 100MB drive for GRUB boot.  It didnt work however, I got this output:

sudo grub-install --root-directory=/media/root /dev/sda2
Probing devices to guess BIOS drives. This may take a long time.
The file /media/root/boot/grub/stage1 not read correctly.

---

### Post by Joshka89 on 2009-09-28
Sorry for double post:

I'm a bit afraid to turn off my computer right now since i dont know if I have screwed up GRUB or not.

If you need some kind of output let me know which one it is. 

For now here is menu.lst which i have not edited since before making the new partitions.:

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
# kopt=root=UUID=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        218c39ea-b7f5-4fa2-9349-cf6c00c4fdcb
kernel        /boot/memtest86+.bin
quiet

title        Windows 7
root        (hd0,2)
makeactive
chainloader    +1
### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

