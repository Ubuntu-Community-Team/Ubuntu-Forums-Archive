---
title: "No Windows in Grub?"
date: 2006-03-08
forum: General Help
---

### Post by The Len on 2006-03-08
I just installed Ubuntu on a separate partition on my hard drive.  When I start up the computer, it attempts to automatically go into Ubuntu.  When I go to the Grub boot menu, Windows isn't even listed.  Any help with this would be greatly appreciated.  I already consulted a friend who is knowledgable about Linux and he couldn't figure it out.

---

### Post by aysiu on 2006-03-08
Is Windows on /dev/hda1?

The output of ```
sudo fdisk -l
``` should tell you. For example, this is mine: ```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1911    15350076    7  HPFS/NTFS
/dev/hda2            1912       19457   140938245    5  Extended
/dev/hda5            1912       18174   130632516   83  Linux
/dev/hda6           18175       18295      971901   82  Linux swap / Solaris
/dev/hda7           18296       19457     9333733+  83  Linux
``` For that, Ubuntu automatically added this to my /boot/grub/menu.lst: ```
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1
``` I'm kind of surprised Ubuntu didn't automatically add it to your menu.lst

---

### Post by The Len on 2006-03-09
Ok, I did the "sudo fdisk -l" and got this:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10124    81320998+  83  Linux
/dev/sda2           10125       24320   114029370    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5           10498       24320   111026128+   7  HPFS/NTFS
/dev/sda6           10125       10497     2996059+  82  Linux swap / Solaris

Partition table entries are not in disk order

I'm not really sure what all that means.... it looks like the "W95 Ext'd (LBA)" is Windows, but Windows XP?

---

### Post by aysiu on 2006-03-09
Actually, it looks to me as if this line is Windows XP: ```
/dev/sda5 10498 24320 111026128+ 7 HPFS/NTFS
``` See how it's NTFS?

Unfortunately, I don't know how the **sd**s figure in Grub. I know **hd**.

Can you boot into Ubuntu and post the output of this command? ```
cat /boot/grub/menu.lst
```

---

### Post by The Len on 2006-03-09
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/sda1 ro

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

title           Ubuntu, kernel 2.6.12-10-amd64-generic Default
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic Default (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro single
initrd          /boot/initrd.img
boot

title           Ubuntu, kernel 2.6.12-9-amd64-generic Previous
root            (hd0,0)
kernel          /boot/vmlinuz.old root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img.old
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-amd64-generic Previous (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz.old root=/dev/sda1 ro single
initrd          /boot/initrd.img.old
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-amd64-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-10-amd64-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.12-10-amd64-generic
boot

title           Ubuntu, kernel 2.6.12-9-amd64-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-amd64-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-amd64-generic root=/dev/sda1 ro single
initrd          /boot/initrd.img-2.6.12-9-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by incubus on 2006-03-09
Yep, aysiu is absolutely right. 
/dev/sda2 10125 24320 114029370 f W95 Ext'd (LBA)

...is an extended partition that (if I read correctly) includes both your windows and swap partitions.

You can add, as aysiu said, that "chainloader" entry to your grub menu.lst. However, I suspect that it won't work and that's the reason why Ubuntu installation failed to that for you. If my memory serves me, Windows is a very jealous system and WANTS to be in the very beginning of your hard drive (first 10Gb) AND be in a primary partition, not logical. If you check aysiu's list, that's what he did in his computer.

I don't know the size of your partitions (too lazy to do the math), but they may not be complying with Microsoft's rules. If that's the case, this is a good opportunity to get rid of windows. :-)

Just kidding, tell us and we will figure out a way of getting that back. You may need to reinstall things, though.

incubus

PS: I could be completely wrong, as I haven't followed the news for a while. It would be nice to have a third and wiser opinion.

---

