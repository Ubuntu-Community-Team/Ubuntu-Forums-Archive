---
title: "Legacy grub question (defoptions)"
date: 2011-02-06
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-02-06
i added the following to my boot option and was wondering if i moved it to the defoptions what would i have to do to the existing options should i also move the quite spash?
nomodeset video=uvesafb:mode_option=1280x720-24
for the record grub2 is hell on my cpu more of a hog than flash
a few examples of defoptions and a the corresponding kernel line should help me with out any explination
/boot/grub/menu.lst:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
timeout        2

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
# kopt=root=UUID=0a2d297f-1e6d-46ab-8209-dcadc233c21d ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0a2d297f-1e6d-46ab-8209-dcadc233c21d

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-28-generic
uuid        0a2d297f-1e6d-46ab-8209-dcadc233c21d
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=0a2d297f-1e6d-46ab-8209-dcadc233c21d ro quiet splash nomodeset video=uvesafb:mode_option=1280x720-24
initrd        /boot/initrd.img-2.6.32-28-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-28-generic (recovery mode)
uuid        0a2d297f-1e6d-46ab-8209-dcadc233c21d
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=0a2d297f-1e6d-46ab-8209-dcadc233c21d ro  single
initrd        /boot/initrd.img-2.6.32-28-generic

#title        Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic
#uuid        0a2d297f-1e6d-46ab-8209-dcadc233c21d
#kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=0a2d297f-1e6d-46ab-8209-dcadc233c21d ro quiet splash 
#initrd        /boot/initrd.img-2.6.32-27-generic

#title        Ubuntu 10.04.1 LTS, kernel 2.6.32-27-generic (recovery mode)
#uuid        0a2d297f-1e6d-46ab-8209-dcadc233c21d
#kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=0a2d297f-1e6d-46ab-8209-dcadc233c21d ro  single
#initrd        /boot/initrd.img-2.6.32-27-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        0a2d297f-1e6d-46ab-8209-dcadc233c21d
kernel        /boot/memtest86+.bin

title           Chainload into GRUB 2
uuid            0a2d297f-1e6d-46ab-8209-dcadc233c21d
kernel          /boot/grub/core.img

### END DEBIAN AUTOMAGIC KERNELS LIST

title         -----------------------------------------------------------
root

title         Fugly Windows 7
root          (hd0,2)
makeactive
chainloader   +1

title         -----------------------------------------------------------
root

title           Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
uuid            decf38bf-6b4d-4acc-90db-0f18760310f5
kernel          /boot/vmlinuz-2.6.32-25-generic root=UUID=decf38bf-6b4d-4acc-90db-0f18760310f5 ro quiet splash
initrd          /boot/initrd.img-2.6.32-25-generic

```

---

### Post by Krytarik on 2011-02-06
Just put it that way:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash nomodeset video=uvesafb:mode_option=1280x720-24

```

---

### Post by pqwoerituytrueiwoq on 2011-02-06
Since you left the line commented out i assume then it is used by the script that generates the menu.lst file and places that on the kernel line a double # would prevent that correct

---

### Post by Krytarik on 2011-02-06
> **pqwoerituytrueiwoq said:**
> Since you left the line commented out i assume then it is used by the script that generates the menu.lst file and places that on the kernel line a double # would prevent that correct
Yes, like itself states:
> ## DO NOT UNCOMMENT THEM, Just edit them to your needs

---

### Post by pqwoerituytrueiwoq on 2011-02-07
thinks, it is so nice to finally have that nvidia boot resolution bug fixed (technically worked around) which also means my ttys are in a reasonable resolution
to anyone looking for the right resolution for that 
hwinfo --framebuffer
it is comes back blank
sudo hwinfo --framebuffer
also that added line requires v86d to be installed

---

