---
title: "get the right entry in grub"
date: 2010-03-19
forum: General Help
---

### Post by X1R1 on 2010-03-19
Hi all, a little help here.

I just installed archlinux to try it out and need to add the entry to Grub.

I formated the hard drive with the a root partition for arch of 42Gb and ubuntu can see it perfeclty.

When I was installing arch I made a mistake and installed grub again, overwriting my previous grub with my ubuntu and windows entries.

So I fixed and got my working grub back with SuperGrubDisk, but now I want to add the ARCHLINUX entry to Grub and dont know how. I have added the previous entries from the grub that ARCH installed and moved the initrd and vmlinuz files to the /boot directory on ubuntu, but it doesnt work. I did a similar thing with Acronis True Image rescue cds(to avoid having to insert the cd in order to use it) and it worked like a charm, but I am lost in this one.

Here are my partitions, sdb is the one where all my partitions and files are (sdb5 is where ARCH is), the other 2 are backups:

> Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda85214c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       31871   256003776    7  HPFS/NTFS
/dev/sda2           31872      243201  1697508225   83  Linux

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x79d357a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       75154   603674473+   7  HPFS/NTFS
/dev/sdb2           75155       91201   128897527+   5  Extended
/dev/sdb5           75155       81014    47070418+  83  Linux
/dev/sdb6           81015       81048      273073+  83  Linux
/dev/sdb7           81049       90953    79561881   83  Linux
/dev/sdb8           90954       91201     1992028+  82  Linux swap / Solaris

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9503c6ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       24792   199141708+   7  HPFS/NTFS


Here is my menu.lst, ARCH entries are at the bottom:

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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/black light-blue/light-gray

#A splash image for the menu
splashimage=/boot/grub/splashimages/splash.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=712ef7a1-d997-4bda-8992-e968c39ddcac ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=712ef7a1-d997-4bda-8992-e968c39ddcac

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

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		712ef7a1-d997-4bda-8992-e968c39ddcac
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=712ef7a1-d997-4bda-8992-e968c39ddcac ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		712ef7a1-d997-4bda-8992-e968c39ddcac
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=712ef7a1-d997-4bda-8992-e968c39ddcac ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, memtest86+
uuid		712ef7a1-d997-4bda-8992-e968c39ddcac
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

#Acronis TrueImage Grub menu.lst entry
title	Acronis TrueImage Home v10.0
uuid	712ef7a1-d997-4bda-8992-e968c39ddcac
kernel /boot/acronis/kernel.dat quiet vga=788 ramdisk_size=40000
initrd /boot/acronis/initrd

#Acronis Grub menu.lst entry kernel.dat & ramdisk.dat from /media/WinXP/Program Files/Acronis/Disk Director
title Acronis Disk Director v10.0
uuid	712ef7a1-d997-4bda-8992-e968c39ddcac
kernel /boot/acronisDD/kernel.dat quiet vga=788 ramdisk_size=40000
initrd /boot/acronisDD/ramdisk.dat

# (0) Arch Linux
title  Arch Linux
root   (hd0,4)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/973c9f3e-7062-4111-87a9-74818855dc23 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,4)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/973c9f3e-7062-4111-87a9-74818855dc23 ro
initrd /boot/kernel26-fallback.img

I think it has something to do with that uuid, so any advice will be appreciatted.

Regards

---

### Post by dcstar on 2010-03-19
> **X1R1 said:**
> Hi all, a little help here.

I just installed archlinux to try it out and need to add the entry to Grub.

I formated the hard drive with the a root partition for arch of 42Gb and ubuntu can see it perfeclty.

When I was installing arch I made a mistake and installed grub again, overwriting my previous grub with my ubuntu and windows entries.

So I fixed and got my working grub back with SuperGrubDisk
........

You should be using grub2 (grub-pc), not the old grub.

---

### Post by spiderbatdad on 2010-03-19
> **dcstar said:**
> You should be using grub2 (grub-pc), not the old grub.

I disagree entirely. Legacy grub isn't going to disappear any time soon, and actually works the way a boot loader is expected to work, unlike the present state of grub-pc.

To the OP: you do not need /dev/disk/by-uuid you can simply use /dev/sdb5, however this entry should be in the automagic kernel section, and the mapping isnt quite right.

You said sdb5 which is equivalent of (hd1,4)

```
# (0) Arch Linux
title Arch Linux
root (hd**1**,4)
kernel /boot/vmlinuz26 root=**/dev/sdb5** ro
initrd /boot/kernel26.img

```

---

### Post by X1R1 on 2010-03-19
spider,

I agree with you too, also I know some commands for this grub and they change a lot in the new one, besides this Ubuntu system is upgraded from jaunty and I would have to add all the manual entries again.

When I do what you suggested I get error 22: No such partition, but when I do the way I had it, I get error 15: file not found.

Should I reinstall arch on the partition and at the end say NOT to install grub?

Reinstalling is a bit of work (you have to tweak lots of settings in an arch installation) so If there is a better solution I will appreciate it.

---

### Post by spiderbatdad on 2010-03-20
not sure why you are getting error 22. Unless the initrd entry didn't match for that partition. I see you have three linux partitions. If you know arch you want to add enrty for is on sdb5, then I would navigate into the file system from Ubuntu (or whatever you can boot) like in /media/.../boot/... somewhere and check the initrd file name. Maybe it is this one: initrd /boot/kernel26-fallback.img
You will need the arch filesystem manually mounted.```
sudo mount /dev/sdb5 /media
```

Below is an example I have on this computer:
```
## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=b13362c7-2789-4b59-83a0-da4771409a70 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-19-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-19-generic root=UUID=b13362c7-2789-4b59-83a0-da4771409a70 ro  single
initrd		/boot/initrd.img-2.6.31-19-generic

title		Debian 2.6.26-2
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sda6
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian 2.6.32-bpo.2-686
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-bpo.2-686 root=/dev/sda6
initrd		/boot/initrd.img-2.6.32-bpo.2-686

#title		Chainload into GRUB 2
#root		(hd0,2)
#kernel		/boot/grub/core.img

#title		Ubuntu 9.10, memtest86+
#root		(hd0,2)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

