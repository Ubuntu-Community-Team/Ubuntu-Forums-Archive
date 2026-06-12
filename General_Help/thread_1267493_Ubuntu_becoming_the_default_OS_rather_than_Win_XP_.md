---
title: "Ubuntu becoming the default OS rather than Win XP and duplicate Win XP in boot menu"
date: 2009-09-15
forum: General Help
---

### Post by mansour2009 on 2009-09-15
Hello:

I installed Ubuntu 9.04 on my Win XP Pro, using a USB Drive as boot device today. Then I installed it permanently on my Hard Drive next to my Win XP. Hoping that I can switch back and forth easily without needing to restart each time I want to switch.

Ubuntu is now my default, I wanted Win XP to be my default OS.
Also there is duplicate line of Win XP there in boot menu.
And lastly, I can't switch unless I restart and choose Win XP.

How would I fix all these?
Greatly appreciate if anyone tell me how. This is my first day ever with Ubuntu.

---

### Post by P4man on 2009-09-16
Hi,

You'll need to edit your grub configuration file. open a terminal (apps > access > terminal) and type

```
gksudo gedit /boot/grub/menu.lst
```

If you paste the contents of that file here, we can help you change it, though if you read through the document, it will explain most things. Change the windows entry to the top and remove the one you dont need (although I suspect one of them is the windows recovery partition, im not sure Id delete it)

---

### Post by Mike_IronFist on 2009-09-16
> **mansour2009 said:**
> Hello:

I installed Ubuntu 9.04 on my Win XP Pro, using a USB Drive as boot device today. Then I installed it permanently on my Hard Drive next to my Win XP. Hoping that I can switch back and forth easily without needing to restart each time I want to switch.

Ubuntu is now my default, I wanted Win XP to be my default OS.
Also there is duplicate line of Win XP there in boot menu.
And lastly, I can't switch unless I restart and choose Win XP.

How would I fix all these?
Greatly appreciate if anyone tell me how. This is my first day ever with Ubuntu.

First, to edit your boot menu, in Ubuntu, go to Add/Remove under the applications menu, and install Kgrubeditor. It allows you to edit your boot menu very easily, in a user-friendly manner.

Second, if you want to Dual Boot, you're going to HAVE TO restart each time you want to switch. Your computer normally doesn't boot into two operating systems at once. It's one or the other on every boot, hence Dual BOOT.

You can't just switch to XP while booted into Ubuntu. You must reboot in order to switch. Sorry.

BUT, if you are interested in running Windows programs on Ubuntu, you may be interested in Wine, a program that allows just that. It doesn't work with every program, some work flawlessly, others not at all, and some work partially, but it all depends on what you need to do.

Once again, to install Wine, you can just go to Add/Remove and search for it. Once it's installed, Windows program binaries ( .exe files) will likely run as they do on Windows (that is, with a double-click).

---

### Post by frlan.jb on 2009-09-16
I was wondering the same thing myself...I'm dual booting Windows Vista/Longhorn and Ubuntu 8.04LTS, I would like to keep Vista as my default OS since I use it the most for school. Here's the contents of my gedit file:




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
# kopt=root=UUID=df3a9c02-760b-40a3-8f33-353c5334747e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,4)
kernel        /vmlinuz-2.6.24-24-generic root=UUID=df3a9c02-760b-40a3-8f33-353c5334747e ro quiet splash
initrd        /initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,4)
kernel        /vmlinuz-2.6.24-24-generic root=UUID=df3a9c02-760b-40a3-8f33-353c5334747e ro single
initrd        /initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,4)
kernel        /memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1

---

### Post by lisati on 2009-09-16
On both my systems that have both Windows and Ubuntu there are two entries for Windows - one is Windows and the other is the recovery partition. On my XP desktop it was obvious which was which, but on my Vista laptop, the entries had the same description. It is a fairly straightforward task to work out which is which and subsequently edit menu.lst

Hope this helps some of those who are baffled by the apparent double-up.

---

### Post by rocket16 on 2009-09-16
For simplicity, try KGrubEditor.

---

