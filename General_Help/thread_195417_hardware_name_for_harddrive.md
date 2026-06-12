---
title: "hardware name for harddrive?"
date: 2006-06-12
forum: General Help
---

### Post by solstice on 2006-06-12
Hey all. I have a window boot on a second harddrive, I installed ubuntu to my first hardrive and grub didn't pick up the boot on the 2nd hard drive. I've been going without windows fine, but, I have an itch to play some games w/ some friends so would like to try to get it booting again. (it can't be too hard)

I can edit my grub file, but I don't know the name of the hard drive I'm trying to hit. I tried (hd0,0), (hd0,1), (hd1,0), (hd1,1). Those seemed like the obvious choices to me. Is there a command I can type to see a list of hardware in my machine? I've checked device manager and I didn't see what I was looking for, but maybe I missed it?

"sudo fdisk -l" gives me

```

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14569   117025461   83  Linux
/dev/hda2           14570       14946     3028252+   5  Extended
/dev/hda5           14570       14946     3028221   82  Linux swap / Solaris

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hdb2            2551       14946    99570870    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    c  W95 FAT32 (LBA)


``` 

It appears the winxp drive/partitions are intact, as they should be.

Any help would be appreciated!

---

### Post by caserio on 2006-06-12
Hi,

Do cat /boot/grub/menu.lst
and post the result here

---

### Post by solstice on 2006-06-12
I tried editing grub from grub itself too, this was helpful because you can hit tab and it will list available drives and partitions, but still no luck.

here is my menu.lst

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title 		Windows XP Professional (Sucks)
rootnoverify	(hd1,0)
makeactive
chainloader 	+1


```

---

### Post by caserio on 2006-06-12
Try this:

title           Windows XP Professional (Sucks)
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

Then reboot

---

### Post by solstice on 2006-06-12
now i'm getting the error:

NTLDR is missing

I could use a windows disk to fixmbr...but I don't want to break my grub menu. thanks for the help so far! any ideas?

Edit: I also tried root (hd1, 1) because there are two partitions on that drive.

---

### Post by pyromithrandir on 2006-06-12
Windows likes to be the first hard drive, and it tries to boot off the first hard drive even if it isn't.
> Try this:

title Windows XP Professional (Sucks)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Then reboot
Using map is the right idea, but shouldn't it go before makeactive? Such as...
> title Windows XP Professional (Sucks)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
I'm not sure, but I think that might be the problem.

---

### Post by caserio on 2006-06-12
Same thing. 

You're right solstice, you have to use a windoze disk to fix mbr and boot into windoze.
You can reinstall grub with your ubuntu disk.  

My menu.lst:
title           Kubuntu, kernel 2.6.15-23-k7
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-k7
savedefault
boot

title           Kubuntu, kernel 2.6.15-23-k7 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-k7 root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.15-23-k7
boot

title           Kubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by solstice on 2006-06-12
Thanks for the help guys, I really appreciate it. Okay, I'm a bit nervous...How will this work?

If I do a fixmbr from the win xp disk, that will break grub, right? Then, if I get grub back on here, won't that overwrite the windows boot record again?

Also, how can I boot back into my linux drive if grub is broken? can I do it from the CD?

---

### Post by solstice on 2006-06-13
I have fixed the boot record for windows. 

Grub is gone :( Can someone tell me how to boot back into linux using the Dapper CD and fix grub? Ubuntu is on first drive, first partition. Windows is on second drive first partition.

I really appreciate the help!

---

### Post by solstice on 2006-06-14
does anyone know now?

---

### Post by erimar77 on 2006-06-14
[http://ubuntuforums.org/showthread.php?t=194434&highlight=reinstall+grub](http://ubuntuforums.org/showthread.php?t=194434&highlight=reinstall+grub)

[http://ubuntuos.com/2006/03/howto-restore-grub](http://ubuntuos.com/2006/03/howto-restore-grub)

---

### Post by solstice on 2006-06-14
to fix the NTLDR is missing error, I did the following:

   1.  Insert the Windows XP bootable CD into the computer.
   2. When prompted to press any key to boot from the CD, press any key.
   3. Once in the Windows XP setup menu press the "R" key to repair Windows.
   4. Log into your Windows installation by pressing the "1" key and pressing enter.
   5. You will then be prompted for your administrator password, enter that password.
   6. Copy the below two files to the root directory of the primary hard disk. In the below example we are copying these files from the CD-ROM drive letter "E". This letter may be different on your computer.

      copy e:\i386\ntldr c:\
      copy e:\i386\ntdetect.com c:\

   7. Once both of these files have been successfully copied, remove the CD from the computer and reboot.

This is after reinstalling both operating systems and getting windows on the first drive, Dapper on the 2nd. Dapper didn't automatcally add windows for some reason, then when I added it manually I got the NTLDR is missing error again. The above steps fixed it.

---

### Post by caserio on 2006-06-14
look [here]("https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub?highlight=%28grub%29%7C%28reinstall%29")

---

