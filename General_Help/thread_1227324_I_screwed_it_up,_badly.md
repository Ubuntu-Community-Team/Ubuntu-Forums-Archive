---
title: "I screwed it up, badly"
date: 2009-07-30
forum: General Help
---

### Post by Fixman on 2009-07-30
I recently bought a Laptop, and it worked perfectly. However, when today I turned it-t boot and on, it didnt boot and grub menu popped the message "unrecognized device string". Thinking on the things I have done before rebooting that could have screwed it, I remembered adding Debian's testing repositories to the computer, and then updating the kernel. Indeed, in a closed look, I noticed all entries f my menu.lst file had "Debian GNU/Linux" as prefix.

I really don't know how to solve this, but to throw chances I hope the new kernel just modifier menu.lst. For some strange reason, the menu.lst file won't change if I reinstall grub from the Live CD, so does someone here have the original "menu.lst" file so I can use it on my computer?

---

### Post by afroman10496 on 2009-07-30
Go to [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and burn it to a CD. Then, back up all your data by accessing your hard drive from an Ubuntu Live CD. After that, wipe your hard drive and do a clean install of Ubuntu. If that fail, try a derivative like Xubuntu ([http://www.xubuntu.org/](http://www.xubuntu.org/)) or Kubuntu ([http://www.kubuntu.org](http://www.kubuntu.org)). Hope it helps:D

---

### Post by lindsay7 on 2009-07-30
Hold off on doing anything yet.  I am seeing a number of people who are experiencing the same thing you are.  Seems like it has to do with the latest update.  There may be more info coming on this today.  If you do a reinstall and it gets upgraded automatically you may end up in the same place.

I would give it some time.

---

### Post by Fixman on 2009-07-30
> **Afroman10496 said:**
> Go to [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and burn it to a CD. Then, back up all your data by accessing your hard drive from an Ubuntu Live CD. After that, wipe your hard drive and do a clean install of Ubuntu. If that fail, try a derivative like Xubuntu ([http://www.xubuntu.org/](http://www.xubuntu.org/)) or Kubuntu ([http://www.kubuntu.org](http://www.kubuntu.org)). Hope it helps:D

Can you please read ALL my post? I know I can format the computer, heck, I don't even know why you want me to download gParted if its already installed in the Live CD. I could also make a partition, install ubuntu there, and check the menu.lst file of it. All I'm asking is for some plain new menu.lst file.

By the way, heres mine:
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
# kopt=root=UUID=2c770149-9cb5-4a06-8e3b-9f55dedf36f4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2c770149-9cb5-4a06-8e3b-9f55dedf36f4

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
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title		Debian GNU/Linux, kernel 2.6.28-14-generic
root		2c770149-9cb5-4a06-8e3b-9f55dedf36f4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=2c770149-9cb5-4a06-8e3b-9f55dedf36f4 ro quiet splash
initrd		/boot/initrd.img-2.6.28-14-generic

title		Debian GNU/Linux, kernel 2.6.28-14-generic (recovery mode)
root		2c770149-9cb5-4a06-8e3b-9f55dedf36f4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=2c770149-9cb5-4a06-8e3b-9f55dedf36f4 ro single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic
root		2c770149-9cb5-4a06-8e3b-9f55dedf36f4
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c770149-9cb5-4a06-8e3b-9f55dedf36f4 ro quiet splash
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-13-generic (recovery mode)
root		2c770149-9cb5-4a06-8e3b-9f55dedf36f4
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2c770149-9cb5-4a06-8e3b-9f55dedf36f4 ro single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic
root		2c770149-9cb5-4a06-8e3b-9f55dedf36f4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c770149-9cb5-4a06-8e3b-9f55dedf36f4 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel 2.6.28-11-generic (recovery mode)
root		2c770149-9cb5-4a06-8e3b-9f55dedf36f4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2c770149-9cb5-4a06-8e3b-9f55dedf36f4 ro single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Debian GNU/Linux, kernel memtest86+
root		2c770149-9cb5-4a06-8e3b-9f55dedf36f4
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

By the way, if I replace all UUIDs with the actual hard drive it starts booting but hangs on "Waiting for root hard disk".

---

### Post by itsamebuddich on 2009-07-30
This sounds like a software issue to me.  The advice given above should work, since your hardware is independent of this.

---

### Post by merlinus on 2009-07-30
> By the way, if I replace all UUIDs with the actual hard drive it starts booting but hangs on "Waiting for root hard disk".

Change these as well:

# kopt=root=UUID=2c770149-9cb5-4a06-8e3b-9f55dedf36f4 ro
# groot=2c770149-9cb5-4a06-8e3b-9f55dedf36f4

---

