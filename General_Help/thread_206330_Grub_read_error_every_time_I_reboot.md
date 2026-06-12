---
title: "Grub read error every time I reboot"
date: 2006-06-29
forum: General Help
---

### Post by LTBookman on 2006-06-29
Hi, after every reboot (either by ctrl+alt+del or anywhere in ubuntu or the bios) I get a grub read error on stage 1.5 that stops the booting process.

I have to turn off and then on the computer instead of reboot, and proceeding that way I don't get any error.

Any ideas why this happens? TIA.

---

### Post by simonn on 2006-06-30
What is the EXACT error?

---

### Post by LTBookman on 2006-06-30
It's "Grub loading Stage 1.5" and after a while "Read error". Then it stops booting.

---

### Post by jtholmes on 2006-06-30
Strange,
stage 2.0 is next, then the menu. sounds like your
bios is loosing track of where the /boot/grub/menu.lst
file is. 
How many hard drives do you have installed

---

### Post by LTBookman on 2006-06-30
[QUOTE=jtholmes]How many hard drives do you have installed[/QUOTE]

Two: the one where Ubuntu -and WXP- is (primary master) and another one for data (primary slave). Data HD used to be secondary slave. I had to change it and this keeps happening since.

---

### Post by simonn on 2006-06-30
Post your /boot/grub/menu.lst here and list your partitions and what's on them (on both disks).

---

### Post by LTBookman on 2006-07-01
Partitions:

Primary master:
-hda1: WindowsXP
-hda2: Ubuntu
-hda5: Swap

Primary slave:
-hdb5: Data

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by simonn on 2006-07-02
That looks ok.

Can you post the results of:

```

ls -l /boot/grub

```

---

### Post by DAXP on 2006-07-02
Just try this real quick:

Use the Ubuntu CD, and use the 'Boot to first Hard Disk' option. I had a Disk Read Errror with Windows once, and a problem with it being unable to find a required driver for startup or something, and doing something like that fixed it. That wasn't a dualboot machine, though, so I'm not sure if it'll work..and you'll need the CD every time you start, if it does. >_<

---

### Post by LTBookman on 2006-07-02
$ ls -l /boot/grub
total 184
-rw-r--r-- 1 root root    197 2006-06-27 20:24 default
-rw-r--r-- 1 root root     15 2005-12-10 18:40 device.map
-rw-r--r-- 1 root root   7508 2006-06-27 20:24 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2006-06-27 20:24 fat_stage1_5
-rw-r--r-- 1 root root   8128 2006-06-27 20:24 jfs_stage1_5
-rw-r--r-- 1 root root   3889 2006-06-15 16:27 menu.lst
-rw-r--r-- 1 root root   3889 2006-06-15 16:27 menu.lst~
-rw-r--r-- 1 root root   6804 2006-06-27 20:24 minix_stage1_5
-rw-r--r-- 1 root root   9076 2006-06-27 20:24 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2006-06-27 20:24 stage1
-rw-r--r-- 1 root root 105428 2006-06-27 20:24 stage2
-rw-r--r-- 1 root root   8764 2006-06-27 20:24 xfs_stage1_5

---

### Post by LTBookman on 2006-07-02
[QUOTE=DAXP]That wasn't a dualboot machine, though, so I'm not sure if it'll work..and you'll need the CD every time you start, if it does. >_<[/QUOTE]

Thanks, but actually I can boot. What I can't do is reboot.

---

### Post by simonn on 2006-07-02
What is happening is that your system cannot find /boot/grub/e2fs_stage1_5 (assuming you have Ubuntu installed an ext2 or 3 file system). 

Your /boot/grub/menu.lst looks fine for your partitioning scheme and the stage files are where they should be. So it is a bit mysterious.

Where is grub installed? MBR on hda?

---

### Post by LTBookman on 2006-07-04
[QUOTE=simonn]Where is grub installed? MBR on hda?[/QUOTE]

Errr... I don't know. Any help on finding that out?

---

