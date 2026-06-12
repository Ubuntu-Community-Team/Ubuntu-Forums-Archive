---
title: "FATAL: module minix not found"
date: 2006-03-15
forum: General Help
---

### Post by can_climber on 2006-03-15
Hello,

  I have been doing quite a bit of searching on the net to find a solution to this problem, but have found no common solutions. This one has kinda stumped me.

I have a dual boot system, with windows on one drive (hda1) (along with the MBR) and linux on another (hdb1).  After selecting any linux kernel or recovery mode I get the errors printed out and no linux!

FATAL: Module minix not found
Mount: mounting /dev/hdb1 or /root failed: no such deivce
Mount: mounting /root/dev on /dev/.static/dev failed: no such file or directory
Mount: mounting /dev on /root/dev failed: no such file or directory

Target filesystem doesn't have /sbin/init

BusyBox v1.00-pre10 (Debian 20046623-1ubuntu) Built-in shell (ash)

Enter "help" for a list of built-in commands/.
/bin/sh: Can't access TTY: job control turned off.
#

So I have a live cd, and i am working off that, my version of ubuntu linux was the most recent update.

Here is the contents of my menu.lst
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.

title		Other operating systems:
root

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

and here is my fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1   /media/windows   vfat   user,fmask=0111,dmask=0000   0   0

also here is my results for fdisk -l:
Disk /dev/hda: 10.2 GB, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1240     9960268+   c  W95 FAT32 (LBA)

Disk /dev/hdb: 4303 MB, 4303272960 bytes
255 heads, 63 sectors/track, 523 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         497     3992121   83  Linux
/dev/hdb2             498         523      208845    5  Extended
/dev/hdb5             498         523      208813+  82  Linux swap / Solaris

I can mount the drive once I boot on the live cd (thats how I got the file data), but I am stumped as to how to fix this. any thoughts would be great....

-Caleb

---

### Post by can_climber on 2006-03-16
ahh yes,  nothing like being a n00b.

ummm. the first time I ran grub-install /dev/hda
but I thought it out and ran grub-install /dev/hda1

a small difference with very different results.  all fixed up now.  this can all be deleted!

---

### Post by Zelut on 2006-03-17
I just had someone bring a laptop into my shop with the same error.  I've assumed its a grub error somehow but wans't sure.  This machine specs are dual-boot on a single drive.  I'm assuming grub would go on /dev/hda?  ...or you said above /hda1.  I'll give it a try.

---

### Post by Ulf Karlsson on 2006-03-31
My friend just got this problem and I figured out what the cause was. Basically you just need to create a new file and you will be OK (until you have bad luck next time). I reported this to the bug tracker:

In the fstype tool there is a problem if the lower 16 bit of number of free inodes in a ext3 filesystem happens to match minix filesystem magic.

This will cause the system not to boot since ubuntu will attempt to mount the filesystem as a minix filesystem.

This problem has been discussed before, but the cause was never investigated, e.g.:

[http://www.ubuntuforums.org/archive/...p/t-95729.html](http://www.ubuntuforums.org/archive/...p/t-95729.html)

Stupid workaround:

mount /dev/sda1 /root
touch /root/newfile
sync

---

### Post by discofro on 2006-06-17
Having the exact same problem now... but getting a new error when I try your workaround. I am getting

Cannot read /etc/fstab: No such file or directory

OR

Cannot read /proc/filesystems: No such file or directory

Running out of ideas here. I want to just do a reinstall but it won't do it unless I format the drive and lose everything. (If this was my computer I would have backed up my data, but not these people I am doing this work for.)

What else can I do?

---

### Post by ifokkema on 2006-06-20
[QUOTE=discofro]Having the exact same problem now... but getting a new error when I try your workaround. I am getting

Cannot read /etc/fstab: No such file or directory

OR

Cannot read /proc/filesystems: No such file or directory

Running out of ideas here. I want to just do a reinstall but it won't do it unless I format the drive and lose everything. (If this was my computer I would have backed up my data, but not these people I am doing this work for.)

What else can I do?[/QUOTE]

You have these errors because it's your / partition, while the above workaround assumes your / partition is just mounted and all.

If I were you, I would toss in the Live CD and backup the data from there.

---

