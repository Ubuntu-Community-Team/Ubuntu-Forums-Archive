---
title: "Can't boot, disturbing error message"
date: 2009-11-14
forum: General Help
---

### Post by litlfrog on 2009-11-14
Last time I was at work my computer wouldn't shut down. When I went to shut down from the login screen, it froze about halfway through. I had to hold in the power button to get it to go all the way down. Now it won't boot in regular or recovery mode. I get the following message. 

> mounting /sys on /root/sys failed: No such file or directory
mounting /dev on /root/dev failed: No such file or directory
mounting /sys on /root/sys failed: No such file or directory
mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg


The system then dumps me to BusyBox built-in shell (ash). Is there anything I can try here?

---

### Post by litlfrog on 2009-11-14
Bump--anyone?

---

### Post by jeb800e on 2009-11-14
Try putting your Ubuntu LiveCd (if you have one) back in your PC. Try re-formatting your hard drive from the LiveCD and reinstall Ubuntu. You can also try a program Called DBAN (dban.org) that nearly completely erases everything off your hard disk. Your hard disk may be crashed also, and thus, unfixable.

---

### Post by MaxIBoy on 2009-11-14
You can reinstall totally if you want, but I think that's cheating.

> **litlfrog said:**
> Last time I was at work my computer wouldn't shut down. When I went to shut down from the login screen, it froze about halfway through. I had to hold in the power button to get it to go all the way down. Now it won't boot in regular or recovery mode. I get the following message. 



The system then dumps me to BusyBox built-in shell (ash). Is there anything I can try here?

Get it to that point and type 
```
ls / 
``` and tell us what the output is.

Could you also do the same for
```
fdisk -l /dev/?d?
```

Also, what is the contents of your /boot/grub/menu.lst? You can get that file using a boot CD (I'm guessing your main OS installation isn't going to let you copy/paste a text file into a forum post :) )

I suspect that your menu.lst file is screwed up and somehow trying to get it to boot from somewhere that doesn't exist. But I need to see it to be sure.

---

### Post by litlfrog on 2009-11-14
What the heck?! I booted from the Live CD to back up my data, restarted the computer, and removed the CD. It started up fine, no issues at all. I must have shut down and restarted the computer five times this morning and it ALWAYS came back to that same error screen. Could booting with the live CD have somehow fixed the menu.lst file?

---

### Post by MaxIBoy on 2009-11-14
It would not have done anything to your menu.lst.

However, did you change any BIOS settings to boot from the CD?

Also, it's possible that the CD reinitialized some firmware for some motherboard device which had gotten corrupted. Linux CDs are kind of famous for being magical in that respect.

---

### Post by litlfrog on 2009-11-14
MaxiBoy, I didn't have to change any BIOS options--it was already set to boot from CD first. Anyway, I'm going to post the outputs you suggested just in case the problem comes back, since I can boot from this computer now.

menu.lst
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=8c6e7747-a008-4ba3-b95f-e3c92ec882f2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=8c6e7747-a008-4ba3-b95f-e3c92ec882f2

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		8c6e7747-a008-4ba3-b95f-e3c92ec882f2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=8c6e7747-a008-4ba3-b95f-e3c92ec882f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		8c6e7747-a008-4ba3-b95f-e3c92ec882f2
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=8c6e7747-a008-4ba3-b95f-e3c92ec882f2 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, kernel 2.6.28-16-generic
uuid		8c6e7747-a008-4ba3-b95f-e3c92ec882f2
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=8c6e7747-a008-4ba3-b95f-e3c92ec882f2 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid		8c6e7747-a008-4ba3-b95f-e3c92ec882f2
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=8c6e7747-a008-4ba3-b95f-e3c92ec882f2 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.10, memtest86+
uuid		8c6e7747-a008-4ba3-b95f-e3c92ec882f2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by litlfrog on 2009-11-14
ls /

> globalnet@globalnet-desktop:~$ ls /
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old


fdisk -l /dev/?d?

> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b542b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7112    57127108+  83  Linux
/dev/sda2            7113        7297     1486012+   5  Extended
/dev/sda5            7113        7297     1485981   82  Linux swap / Solaris


---

### Post by undecim on 2009-11-14
> **litlfrog said:**
> What the heck?! I booted from the Live CD to back up my data, restarted the computer, and removed the CD. It started up fine, no issues at all. I must have shut down and restarted the computer five times this morning and it ALWAYS came back to that same error screen. Could booting with the live CD have somehow fixed the menu.lst file?

It was probably a broken filesystem. When you went to get your data back, the error was probably fixed when the filesystem mounted.

If I were you, I would use a livecd to run fsck on each filesystem, just in case there is an error that both you and the computer aren't noticing.

---

### Post by jeb800e on 2009-11-14
You can also boot up into the livedisk and run FSCK.

---

