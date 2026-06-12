---
title: "Fixing Vista Grub menu"
date: 2009-07-10
forum: General Help
---

### Post by skunkrecords on 2009-07-10
Hey guys,
I've tried to figure out how to do this on my own, but I can't seem to get it. I got a new hard drive, and installed ubuntu, and my Vista hard drive doesn't seem to boot up? 

Here's my fdisk output
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000094e1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5107    41021946   83  Linux
/dev/sda2            5108       60801   447362055    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb95e77d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    6  FAT16
/dev/sdb4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb84a648

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3120    25058304    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2            3120       14594    92158976    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

```

Here's my menu.lst
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
default		saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color black/green white/green

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
password --md5 $1$3sXg5/$Qjcy3KI//uw.sW/Zm2/uR/
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
# kopt=root=UUID=2795be75-8a41-4269-89a3-da80f68e3497 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=2795be75-8a41-4269-89a3-da80f68e3497

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
# defoptions=splash vga=796

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
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false


## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		2795be75-8a41-4269-89a3-da80f68e3497
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2795be75-8a41-4269-89a3-da80f68e3497 ro splash vga=796 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		2795be75-8a41-4269-89a3-da80f68e3497
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=2795be75-8a41-4269-89a3-da80f68e3497 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		2795be75-8a41-4269-89a3-da80f68e3497
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2795be75-8a41-4269-89a3-da80f68e3497 ro splash vga=796 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		2795be75-8a41-4269-89a3-da80f68e3497
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=2795be75-8a41-4269-89a3-da80f68e3497 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows Vista (loader)
rootnoverify	(hd2,1)
savedefault
makeactive
map		(hd1) (hd2)
map		(hd2) (hd1)
chainloader	+1

```

Thanks for the help!

---

### Post by Jebtrix on 2009-07-10
Try this:

title		Windows Vista (loader)
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

---

### Post by KamalGurung on 2009-07-10
I also have same problem, I have two hard disk and I had vista installed on the first one I then added another 120 GB hard disk and installed Linux on it now when I boot from the Linux installed harddisk it shows the Window Vista (loader) but whenever I enter it it says some message and then reboots. I don't know how to use the fdisk to show the output.

Here's my menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=5b51e40a-1aea-4c87-bf6d-57cbdd31c55b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5b51e40a-1aea-4c87-bf6d-57cbdd31c55b

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
title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            5b51e40a-1aea-4c87-bf6d-57cbdd31c55b
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=5b51e40a-1aea-4c87-bf6d-57cbdd31c55b ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            5b51e40a-1aea-4c87-bf6d-57cbdd31c55b
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=5b51e40a-1aea-4c87-bf6d-57cbdd31c55b ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, memtest86+
uuid            5b51e40a-1aea-4c87-bf6d-57cbdd31c55b
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


```

---

### Post by skunkrecords on 2009-07-10
> **Jebtrix said:**
> Try this:

title		Windows Vista (loader)
rootnoverify	(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

I get the message NTLDR is missing. Could that be the wrong partition?

---

### Post by Jebtrix on 2009-07-10
Try (hd2,1) instead.

---

### Post by Jebtrix on 2009-07-10
Actually it could be this also

title Windows Vista (loader)
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2) <-- remove
map (hd2) (hd0) <-- remove
chainloader +1

---

### Post by merlinus on 2009-07-10
IIRC, vista and win7, unlike xp and 2000, do not use NTLDR.

What is the booting order of your hdds in bios?

---

### Post by Jebtrix on 2009-07-11
Yeah I was just going to ask why isn't it saying Bootmgr.exe is missing if its Vista..

---

### Post by skunkrecords on 2009-07-11
> **Jebtrix said:**
> Actually it could be this also

title Windows Vista (loader)
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2) <-- remove
map (hd2) (hd0) <-- remove
chainloader +1

Tried this, then once I try and boot from Vista, my screen displays the text "Starting up..." and doesn't do anything. Same results when I change rootnoverify (hd2,0) to rootnoverify (hd2,1).

My boot order is 
1) WDC WD5000
2) CD/DVD

---

### Post by merlinus on 2009-07-11
So you only are booting one hdd?  If so, then vista must be on sda2.

If that is the case, try this entry in menu.lst:

title Vista
rootnoverify (hd0,1)
makeactive
chainloader +1

and you may have to move the boot flag from sda1 to sda2.

---

### Post by skunkrecords on 2009-07-11
> **merlinus said:**
> So you only are booting one hdd?  If so, then vista must be on sda2.

If that is the case, try this entry in menu.lst:

title Vista
rootnoverify (hd0,1)
makeactive
chainloader +1

and you may have to move the boot flag from sda1 to sda2.

Tried this, and I get the message "BOOTMGR is missing". How do I move the boot flag?

---

### Post by merlinus on 2009-07-11
Use gparted, either on the live ubuntu cd or get it via Applications/Add Remove. Right-click on the partition, choose manage flags, and tick (or untick) boot.

Given the missing bootmgr message, this is clearly your vista partition.

---

### Post by skunkrecords on 2009-07-11
Didn't seem to do the trick. I'm going to try my Vista disk and try to recover it.

---

### Post by Jebtrix on 2009-07-11
```
Tried this, then once I try and boot from Vista, my screen displays the text "Starting up..."
``` 

Finally got a vbox setup like your situation. I got the same Starting up... lockup, it was corrected with a proper map (hdx) (hdx) but the rest was right. If he installed two different OSs on two different drives, each drive would have a boot flag, I don't think its that.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5107    41021946   83  Linux
/dev/sdb4   *           1           1           0    0  Empty
/dev/sdc1   *           1        3120    25058304    7  HPFS/NTFS
 
Boot flags already there.

---

### Post by Jebtrix on 2009-07-11
Skunkrecords are you editing the menu.lst everytime or are you editing the grub entry temporarily in the actual grub boot loader?

---

### Post by Jebtrix on 2009-07-11
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244196352    6  FAT16
/dev/sdb4   *           1           1           0    0  Empty

This definitely isnt right. 250GB Fat16?? I think that may be Vista. 

Check this:
[http://ubuntuforums.org/showthread.php?t=933283](http://ubuntuforums.org/showthread.php?t=933283)

Skunkrecords, you have a 500G, 250G, 120G. Did you install Vista on 250G, or 120G drive?? What exactly do you have installed on all these..lol

---

### Post by merlinus on 2009-07-11
After re-reading this thread, it seems that vista must be on sdc1, but perhaps the problem is due to the order of the hdds in bios.  It also may be because of where grub got installed to, as well.

And perhaps bootmgr.exe got corrupted, so using recovery from the vista cd will at least let the OP boot into it.

Once all this is sorted, then reinstalling grub should fix the problem.

---

### Post by skunkrecords on 2009-07-12
Thanks all for the help! I got it working when I changed the boot flag, and reordered my HDD in the bios. It turned out I needed to fix the boot with my Vista disk.. I remembered why I use ubuntu.. When I added my new HDD my OEM vista disk interpreted it as a hardware change, and now I need to reactivate vista :mad:
Thanks again for all the help!

---

### Post by merlinus on 2009-07-12
Excellent news!  Good on you for sticking with the lengthy process, and hopefully you learned some things you can use to help others.

---

### Post by skunkrecords on 2009-07-12
oh and vista was installed on the 120gb drive :lolflag:

---

