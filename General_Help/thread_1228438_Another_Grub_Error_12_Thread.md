---
title: "Another Grub Error 12 Thread"
date: 2009-07-31
forum: General Help
---

### Post by AxelMan0 on 2009-07-31
I'm not sure if this should go under 'installation and upgrades' but here's my problem.

I've looked around at the various error 12: invalid device requested threads all over google and it seems that everyone's problem is slightly different and none of them quite apply.

I recently installed a third OS on my system--Ubuntu 8.10--on hd0,4 (the order of my partitions is 0, 4, 2, 3 if that is of any significance). During the install I chose manual when asked how to partition my drive and I chose not to install the bootloader (since I already have grub dual booting Jaunty and Vista). However when I try to boot Intrepid it gives me the infamous error 12 message.

Here is my /boot/grub/menu.lst

Oh and if anyone knows how to make .conf files readable by windows without having to go and highlight all the little boxes one by one and press the enter key I'm all ears (my Jaunty is kaput it's one of the reasons I'm trying to get Intrepid to work).

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
# kopt=root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet

## default grub root device
## e.g. groot=(hd0,0)
# groot=8a59b1fa-3729-41ea-b2e2-970421d58ce5

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
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu 8.10
root (hd0,4)
makeactive
chainloader +1

title Windows Vista
root (hd0,1)
makeactive
chainloader +1



From my understanding Grub boots windows slightly differently? Because of this my guess is that the Intrepid entry shouldn't look exactly like the Vista entry and should look more like the above Jaunty entries. Do I have to specify the kernel and uuid like in the other Ubuntu boot options? I noticed the Linux example provided at the top and it has a 'kernel' entry so I just need to know what to put there.

---

### Post by AxelMan0 on 2009-08-01
Ok this is what I've got so far

title Ubuntu 8.10
root (hd0,3)
kernel /boot/vmlinuz(kernel # here) root=/dev/hda4 ro
boot

I get a message telling me to append a correct 'root=' when I try and boot up. I'm getting closer! I'll try some trial and error and see if that works.

---

### Post by RJ12 on 2009-08-01
try adding a "=" (without quotes) if that dosent work add the UUID

---

### Post by AxelMan0 on 2009-08-01
Where can I find the UUID? (p.s. I've since gotten rid of 'ro' since I was only mimicking other posts and don't know what it accomplishes (I'm assuming read-only but I don't know why that would be any advantage on booting), tried replacing the 4 with a 0 and then a 1 after I realized 0 can't possibly work haha, and tried **_s_**da4 instead of **_h_**da4)

---

### Post by merlinus on 2009-08-01
```
blkid
```

And while you are at it, post results of

```
sudo fdisk -l
```

---

### Post by AxelMan0 on 2009-08-01
lol beat you to it. I did a 'sudo blkid' and it showed me everything i needed to know. Ladies and gentlemen, a fully functioning boot entry!

title Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        b6a8cdce-ef21-4689-9a9d-4bc5e1f75fe1
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=b6a8cdce-ef21-4689-9a9d-4bc5e1f75fe1
initrd        /boot/initrd.img-2.6.27-7-generic

I'm not sure if the initrd is needed but it was included in all of the default entries so I figured I might as well put it there. I also deleted 'boot' from the end.

---

