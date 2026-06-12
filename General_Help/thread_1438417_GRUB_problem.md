---
title: "GRUB problem"
date: 2010-03-25
forum: General Help
---

### Post by ProfessionalOPs on 2010-03-25
i was just wondering......

If i change my menu.lst for grub to this:

```
[noparse]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=5ca3a75b-50a7-4d4a-a647-6e07b4515974 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5ca3a75b-50a7-4d4a-a647-6e07b4515974

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

# This is a divider, added to separate the menu items below from the Debian
# ones.
title                                          >>>>>Pauls Boot Options:<<<<<
root

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        -----UNIX operating systems:-----
root

title        >>>>LINUX (Ubuntu 9.04, kernel 2.6.28-18-generic)
uuid        5ca3a75b-50a7-4d4a-a647-6e07b4515974
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=5ca3a75b-50a7-4d4a-a647-6e07b4515974 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        >>>>Linux Recovery
uuid        5ca3a75b-50a7-4d4a-a647-6e07b4515974
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=5ca3a75b-50a7-4d4a-a647-6e07b4515974 ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        >>>>Linux Memory Test
uuid        5ca3a75b-50a7-4d4a-a647-6e07b4515974
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        -----DOS operating systems:-----
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        >>>>Windows 7 Ultimate 
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        >>>>Windows Recovery
rootnoverify    (hd0,1)
savedefault
chainloader    +1[/noparse]
```


will an update with a new kernel corrupt this menu.lst

So basically what im wondering is if  a new kernel is installed and added to the menu.lst will it screw up the file or will i be able to just switch the entries out and it will work fine?    

Any info appreciated THanks

---

### Post by ProfessionalOPs on 2010-03-25
the smiles were just what ubuntu forums put there the are not really there.....lol

---

### Post by bodhi.zazen on 2010-03-25
> **ProfessionalOPs said:**
> the smiles were just what ubuntu forums put there the are not really there.....lol

You should be fine. Never hurts to have a backup though ...

sudo cp /boot/grub/menu.1st /root

and use [noparse], I will fix it for you ...

---

### Post by ProfessionalOPs on 2010-03-25
Ok thankyou....... I actually forgot to back up the original menu.let but when the new kernal is added to the file it just makes it the default and inserts that boot option at the top......so theoretically i should just be able to rename it's title respectively and it will do the same thing as my current menu.lst

correct me if I'm wrong but I think it will work fine??!

---

### Post by thesenu on 2010-03-25
it automatically recovered when you updated it

---

