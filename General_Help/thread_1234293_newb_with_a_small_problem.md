---
title: "newb with a small problem"
date: 2009-08-07
forum: General Help
---

### Post by lift lifted on 2009-08-07
Hi everyone. I'm new to ubuntu, so far I'm loving it. My only problem is that when I start my computer it shows two installations of ubuntu. I logged into both of them, but it seems like they are the same. I guess grub just shows two options. Is there a simple way to get rid of this?

---

### Post by michy99 on 2009-08-07
It is probably two different kernals. Post the contents of the file /boot/grub/menu.lst and we can tell for sure.

---

### Post by lildigiman on 2009-08-07
My Ubuntu has always been that way, and if you look at the name the kernals are different by one or 2 numbers. It is normal and has never caused any issues. I always use the newest kernal.

---

### Post by lift lifted on 2009-08-07
I'm guessing this is what you need. I also found [this]("http://images.google.com/imgres?imgurl=http://www.howtogeek.com/wp-content/uploads/2007/09/image55.png&imgrefurl=http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/&usg=__DfrD_GcGwGJdwY1M-bMFWeAFHXU=&h=275&w=640&sz=45&hl=en&start=1&um=1&tbnid=5wJxVb7cKSkAoM:&tbnh=59&tbnw=137&prev=/images%3Fq%3D/boot/grub/menu.lst%26hl%3Den%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:unofficial%26sa%3DN%26um%3D1"). That's how it looks for me except there's 2 instead of three. I'm not sure if I have the same problem though.

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
# kopt=root=UUID=e6be0c70-5426-4022-ac5a-9072b82a982b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e6be0c70-5426-4022-ac5a-9072b82a982b

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

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        e6be0c70-5426-4022-ac5a-9072b82a982b
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=e6be0c70-5426-4022-ac5a-9072b82a982b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        e6be0c70-5426-4022-ac5a-9072b82a982b
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=e6be0c70-5426-4022-ac5a-9072b82a982b ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e6be0c70-5426-4022-ac5a-9072b82a982b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e6be0c70-5426-4022-ac5a-9072b82a982b ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e6be0c70-5426-4022-ac5a-9072b82a982b
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e6be0c70-5426-4022-ac5a-9072b82a982b ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e6be0c70-5426-4022-ac5a-9072b82a982b
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1

---

### Post by lildigiman on 2009-08-07
Yeah thats perfectly normal, notice that one is the "kernel 2.6.28-14-generic" and the other is  "kernel 2.6.28-11-generic"

---

### Post by MTGap on 2009-08-07
It's like this way in case one kernel doesn't upgrade correctly or becomes broken, then you can just use the other kernel. It's a good idea to always use the newer kernel your: 2.6.28-14

---

### Post by lift lifted on 2009-08-07
oh okay cool. I thought I screwed up the installation. Thanks for your help guys.

---

### Post by Snoober on 2009-08-07
Awesome! I didn't notice that before. Another reason to love Ubuntu/Linux.

---

