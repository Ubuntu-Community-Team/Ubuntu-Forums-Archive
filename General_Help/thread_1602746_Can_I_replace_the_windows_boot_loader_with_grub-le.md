---
title: "Can I replace the windows boot loader with grub-legacy?"
date: 2010-10-21
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-10-21
or make windows boot from inside an extended partition?
Partition Layout:
[[IMG]http://i52.tinypic.com/34ffdw0_th.png[/IMG]]("http://i52.tinypic.com/34ffdw0.png")
The Win_XP partition has win 7 32bit on it.
The Win_7 partition has win 7 64 bit on it.
Is there a way i can boot the Win_7 partition without using the boot loader on the Win_XP partition.
THERE IS NO XP INSTALL IT IS MISS LABLED

---

### Post by pqwoerituytrueiwoq on 2010-10-21
menu.lst
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
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color green/black yellow/brown

#A splash image for the menu
#splashimage (hd0,0)/boot/grub/splashimages/lava.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
#password --md5 $1$bvsOZ/$cC5ILBMyorrInWbmuGR.v1
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
# kopt=root=UUID=decf38bf-6b4d-4acc-90db-0f18760310f5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=decf38bf-6b4d-4acc-90db-0f18760310f5

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
# defoptions=splash vga=769 quiet

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

title           Ubuntu 10.04 LTS, kernel 2.6.32-25-generic
uuid            decf38bf-6b4d-4acc-90db-0f18760310f5
kernel          /boot/vmlinuz-2.6.32-25-generic root=UUID=decf38bf-6b4d-4acc-90db-0f18760310f5 ro quiet splash
initrd          /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04 LTS, kernel 2.6.32-25-generic (recovery mode)
uuid        decf38bf-6b4d-4acc-90db-0f18760310f5
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=decf38bf-6b4d-4acc-90db-0f18760310f5 ro single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        decf38bf-6b4d-4acc-90db-0f18760310f5
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title        ---------------------------------------------------------------------
root

title        Microsoft Windows XP Professional
root        (hd0,2)
makeactive
chainloader    +1
```

---

### Post by Mark Phelps on 2010-10-21
In a word -- NO.  

If you installed Win7 after XP was already there, Win7 finds the partition with the XP boot loader in it and adds the Win7 boot loader files.

If you install EasyBCD into Win7, downloaded from the NeoSmart Technology forums, you can use that to MOVE the Win7 boot loader files to the Win7 partition.

But you REQUIRE an MS Windows boot loader for an MS Windows OS.  All GRUB will do is hand off control to the partition; it can not actually boot an MS Windows OS.

---

### Post by perspectoff on 2010-10-21
What the?

Why (and how) did you squeeze Windows 7 into a 10 Gb partition? It won't run in that -- the pagefile alone is bigger than the free space you have left. You need about 30 Gb to run Windows 7, really.

Windows XP might be able to get away with 20 Gb, but again, if you're only giving it 10 Gb, what's the point?

---

### Post by pqwoerituytrueiwoq on 2010-10-21
> **perspectoff said:**
> What the?

Why (and how) did you squeeze Windows 7 into a 10 Gb partition? It won't run in that -- the pagefile alone is bigger than the free space you have left. You need about 30 Gb to run Windows 7, really.

Windows XP might be able to get away with 20 Gb, but again, if you're only giving it 10 Gb, what's the point?
i did and it booted i did not mess with it farther
i just selected the partition and clicked next and it installed
i want to have windows entirely in a extended partition
i have 4gb of ram
it could have set itself to use the the virtaulMachines partition for a paging file

It gives a warning and just goes about the install

---

### Post by pqwoerituytrueiwoq on 2010-10-21
edited 1st post (added new line 1)

---

### Post by oldfred on 2010-10-22
I have seen some of the advanced users get XP to boot from an extended partition but windows is designed to boot from a primary partition. Boot flags determine which windows partition to boot and boot flags are supposed to be only on primary partitions. Only a second install of windows can be in a logical partition, but it boots thru the windows install in the primary.

Info on how windows multiboots:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

