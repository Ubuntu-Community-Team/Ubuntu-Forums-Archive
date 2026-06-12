---
title: "Vista won't load after ubuntu"
date: 2009-07-13
forum: General Help
---

### Post by ddivney on 2009-07-13
I have an HP pavilion dv3510nr, and it came preinstalled with Vista Home Premium. Not my favorite OS, but I worked with it and I have all my stuff there. After a brief test of running Ubuntu virtually (using VirtualBox), I decided to take Windows 7 of a partition and install ubuntu instead. I did, and it worked. Unfortunately Vista doesn't anymore. Whenever I try to load it, it gives a "windows is loading files" screen, followed by a normal vista loading screen, then it flashes a blue screen with a command prompt silhouette, and finally gives me a recovering tool made by HP, which is of no help whatsoever. I've tried configuring grub to boot Vista, but it just won't work. Any feedback is appreciated.

p.s: I installed Ubuntu 2 days ago and realized Vista doesn't work today :icon_frown:, so consider me a linux noob (albeit a quick learner, I promise).

---

### Post by merlinus on 2009-07-13
Post results of these commands entered in a terminal window:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by lisati on 2009-07-14
Yup - sure sounds like *something* got messed up somewhere, which I can relate to. I've had an installation of Ubuntu going haywire on a machine with XP & a recovery partition - my troubleshooting for the ensuing problems was hindered by my installing SP3 prior to Ubuntu without realising that I needed to install a patch from Compaq/HP first. (I'm not necessarily saying that this is the case for you.)

Does running *fdisk -l* provide any clues as to what's on your machine's partitions? (Edit: merlinus beat me to it, good suggestion about the menu.lst as well, my excuse is that I was talking with Mrs Lisati and listening to something on TV while typing)

---

### Post by ddivney on 2009-07-14
##sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3833069c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33322   267653084   82  Linux swap / Solaris
/dev/sda2           33323       37698    35150220    5  Extended
/dev/sda3           37699       38913     9751552    7  HPFS/NTFS
/dev/sda5           33323       37698    35150188+  83  Linux

##cat /boot/grub/menu.lst

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
# kopt=root=UUID=555f8d31-884c-46f0-846e-73836c8f8a1c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=555f8d31-884c-46f0-846e-73836c8f8a1c

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

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        555f8d31-884c-46f0-846e-73836c8f8a1c
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=555f8d31-884c-46f0-846e-73836c8f8a1c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        555f8d31-884c-46f0-846e-73836c8f8a1c
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=555f8d31-884c-46f0-846e-73836c8f8a1c ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        555f8d31-884c-46f0-846e-73836c8f8a1c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=555f8d31-884c-46f0-846e-73836c8f8a1c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        555f8d31-884c-46f0-846e-73836c8f8a1c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=555f8d31-884c-46f0-846e-73836c8f8a1c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        555f8d31-884c-46f0-846e-73836c8f8a1c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1



##thanks for the quick reply btw

---

### Post by merlinus on 2009-07-14
Try moving the boot flag to sda3.  You can probably use gparted to do this.

The entry in menu.lst is correct.

If this does not help, then we can try reinstalling grub.

---

### Post by ddivney on 2009-07-14
I want to try moving the boot flag, but i have no idea how (sorry). I'll give it a shot, and let you know how it went soon.

---

### Post by ddivney on 2009-07-14
Alright, so I installed gparted and am looking at my partitions. Vista is on sda1, but it tells me it's a "linux-swap". sda3 is a recovery partition premade by HP.
Any ideas?

---

### Post by ddivney on 2009-07-14
Boot flag is on sda1 (vista) by the way.

---

### Post by itsjareds on 2009-07-14
It looks like you put the swap partition as the first partition on your disk. Did you happen to move your Vista partition over to the right a little bit to allow some space for that swap partition?

Sometimes moving a partition can mess up, it corrupted my Windows 7 partition. Thankfully I was still able to read the partition and save my data, but I had to reinstall it.

edit: According to fdisk, your boot flag is on your swap partition. Move it to sda3, which is your NTFS (Windows) partition.

ps: Please wrap any long terminal outputs inside [CODE] tags.

---

### Post by Oscar07202 on 2009-07-14
I had a similar problem before and I was able to fix it by using supergrub.


Description:

Super Grub Disk is a bootable floppy or CDROM that is oriented towards system rescue, specifically for repairing the booting process. Super Grub Disk is simply a Grub Disk with a lot of useful menus. It can activate partitions, boot partitions, boot MBRs, boot your former OS (Linux or another one) by loading menu.lst from your hard disk, automatically restore Grub on your MBR, swap hard disks in the BIOS, and boot from any available disk device. It has multi-language support, and allows you to change the keyboard layout of your shell. 



http://sourceforge.net/projects/freshmeat_supergrub/files/<<<<<<<<<<<Someone provide supergrub homepage, I posted this one cause I trust sourceforge.net

---

### Post by merlinus on 2009-07-14
Tres interessant, n'est pas?

In that case, try changing this:

title        Windows Vista
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader    +1

to this:

title        Windows Vista
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

and leave the boot flag alone.

---

### Post by ddivney on 2009-07-14
Vista is aaaaaaaaalllllll the way to the left... any way to disable "linux-swap"? I'm willing to give supergrub a try, but I want to see if there's anything more simple out there.

---

### Post by ddivney on 2009-07-14
already tried (hd0,0), but it gave an error. I'll try it again and let you know which one exactly

---

### Post by itsjareds on 2009-07-14
This doesn't make sense if fdisk reports your swap on block 1 and being the first partition. It sounds like your Vista partition is on 3.. I could be wrong though (wouldn't be the first time)

---

### Post by merlinus on 2009-07-14
Post a screenshot of gparted.  Another view of the situation might be helpful...

---

### Post by ddivney on 2009-07-14
changing it to (hd0,0) yields the same result...

here's the screenshot

---

### Post by merlinus on 2009-07-14
Can you boot into vista?  If not, try supergrub to at least see if it works.

[http://supergrubdisk.org](http://supergrubdisk.org)

---

### Post by itsjareds on 2009-07-14
Something's definitely wrong here, and Linux is probably not detecting the partitions correctly. Is it just me, or does this guy have a 255GB swap?

---

### Post by merlinus on 2009-07-14
Yeah, tres bizarro....

Or something is fooling both fdisk and gparted....

---

### Post by itsjareds on 2009-07-14
Either way, even if fdisk is incorrect, my bet is that grub will be incorrect as well. He should go with what fdisk says.

---

### Post by merlinus on 2009-07-14
In that case, however, vista is trashed, and has been overwritten by a linux swap partition!

Clearly sda3 is some sort of recovery partition, and even if bootable will want to overwrite what is on sda1.

---

### Post by itsjareds on 2009-07-14
Where is sda4? Maybe it's a hidden partition?

edit: Or maybe it was deleted. Nevermind.

---

### Post by ddivney on 2009-07-14
hi guys, I'm back from my brief adventure with supergrub. I used it to try to boot vista, and then it hit me. If it reaches the Vista loading screen and HP recovery tool, then it must be booting part way. That means that the swap must be the problem right? Feel free to correct me.

---

### Post by merlinus on 2009-07-14
Logical partitions start at 5, so sda4 is not missing.

For example, I have one primary partition, sda1. sda2 is an extended, with sda5, sda6, and sda7 as logicals within that.  sda3 and sda4 do not exist.

---

### Post by merlinus on 2009-07-14
It is booting into your recovery partition, and that is all.  For some reason, whilst you were adding/deleting partitions, vista got formatted as linux swap.  As they say, hasta la vista...

At this point it may be best to cut your losses and start afresh.  Hopefully you have backups of important data.

If not, you might try testdisk to recover data within sda1.

---

### Post by ddivney on 2009-07-14
Oh well... Here's where the HP recovery tool comes in handy ;). Thanks for all the help guys, I appreciate it.=D>=D>=D>

---

### Post by nmaster on 2009-07-14
maybe try this:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by ddivney on 2009-07-14
thanks, I actually will! Before I mess up again, should I just delete the partiton? or do I format it?

---

### Post by itsjareds on 2009-07-14
Formatting should do fine. If you're going to put any form of Windows on it, format it to NTFS.

But be careful, first try to recover it if you can. Formatting should be your last option if you have no chance of recovery.

---

