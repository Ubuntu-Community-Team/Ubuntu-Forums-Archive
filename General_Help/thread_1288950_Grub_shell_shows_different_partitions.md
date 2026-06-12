---
title: "Grub shell shows different partitions"
date: 2009-10-12
forum: General Help
---

### Post by Jaraxle on 2009-10-12
Hello, I have a question about the Grub shell and some more general questions about using Grub. I have the following partitions on my drive (from FDISK):

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60446044

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       31871   256003776    7  HPFS/NTFS
/dev/sda2           31872       60801   232380225    5  Extended
/dev/sda5           31872       59702   223552476   83  Linux
/dev/sda6           60675       60801     1020096   82  Linux swap / Solaris
/dev/sda7           59703       60674     7807558+  83  Linux

Partition table entries are not in disk order

```

Where sda5 is my main Ubuntu 9 install, sda7 is an install of Xubuntu 8, and sda1 is an install of Windows XP. It should be noted that sda5 and sda7 are both under the Extended partition of sda2.

However, if I run sudo grub, and then run find /boot/grub/stage1, I get the following result:

```
find /boot/grub/stage1
 (hd0,4)
 (hd0,6)

```

I assumed that hd0,4 is actually sda partition 5 and that hd0, 6 is really sda partition 7 and this turned out to be correct.

My question is this: what is causing the grub shell to display these numbers? Is it the Extended partition that is throwing off the numbers by 1?

I also just noticed the line displayed at the bottom of the output from fdisk that says "Partition table entries are not in disk order." Is that what is causing it? And if so, how do I view the "real" partition numbers? I thought FDISK would be the final authority and that if anything would be incorrect it would be grub.

As you can see I am confused about this! I also have a couple more questions I will post shortly.

---

### Post by Bucky Ball on 2009-10-12
This result is correct. hd counting starts at 0. You obviously have two grub stage1 files (one for each Linux install). You need to find which one your booting from and add the partition of the other install to that in:

```
/boot/grub/menu.lst
```.

hd(0,4) = sda5
hd(0,6) = sda7

NB:
hd(0,0) = sda1

hd(1,0) = sd**b**1 - (if you had a second drive).

All looks present and correct as far as this goes.

---

### Post by Jaraxle on 2009-10-12
I was booting from /dev/sda7 after the install of Xubuntu on sda7. This was also my default boot option.

What I wanted to do was go back to using Grub on sda5 so that the default boot option would once again be set to Ubuntu. I tried to edit menu.lst manually but could not figure out what was causing Xubuntu to be the default boot item.

So, I ran the following commands from the Grub shell:

```
root (hd0,5)
```

then

```
setup (hd0,5)
```

This reinstalled Grub back to the sda5 partition and set my default back to Ubuntu. I then thought I would be able to run update-grub and have it detect Xubuntu on sda7 but it did not work. Will I have to manually edit menu.lst?

Also, do you think you could tell me what was causing my default OS to be Xubuntu? I know it was because I installed that OS last but what I mean is that I do not understand the numbering system in my menu.lst. I will copy and paste below. As you can see, the default was set to 4 (Ubuntu) but it was booting option 0 (Xubuntu):

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
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=UUID=91b5b6ed-00c0-4905-b5aa-248b05ff7669 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=792

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
# howmany=1

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

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-24-generic root=UUID=91b5b6ed-00c0-4905-b5aa-248b05ff7669 ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda5)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=740a8dea-6119-481a-93c7-5401e3209d40 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
# title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda5)
# root		(hd0,4)
# kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=740a8dea-6119-481a-93c7-5401e3209d40 ro single 
# initrd		/boot/initrd.img-2.6.28-11-generic
# savedefault
# boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
# title		Ubuntu 9.04, memtest86+ (on /dev/sda5)
# root		(hd0,4)
# kernel		/boot/memtest86+.bin  
# savedefault
# boot

```

---

### Post by Bucky Ball on 2009-10-12
You should be able to use the entry for Xubuntu from the /boot/grub/menu.lst in Xubuntu in the menu.lst in Ubuntu. The easiest way to use Xubuntu would have been to load Xfce4-core or xubuntu-desktop from Synaptic into your existing install of Ubuntu and choose Xfce at login from the 'Sessions' menu.

They are both Ubuntu using different desktop environments and a few more or few less and few different packages. Ubuntu Gnome default and Xubuntu Xfce. You can install ubuntu-desktop in Xubuntu conversely which would install the Gnome requirements and dependencies. Your kinda booting two versions of the same operating system (unless you want them to be completely separate for reasons of speed or use).

As for 'default 4', don't know. To get an option for your other partition in grub though, copy from sda7 or copy the one for sda5 and make the appropriate changes. You need to change the parts in bold:

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda**7**.
title        Xubuntu **(call it what you want though)**
root        (hd0,**6**)
kernel        /boot/**vmlinuz-2.6.28-11-generic root=UUID=740a8dea-6119-481a-93c7-5401e3209d40** ro quiet splash 
initrd        /boot/**initrd.img-2.6.28-11-generic**
savedefault
boot
```You should find the appropriate details for 'kernel' and 'initrd' in the /boot directory on sda7. You could change the one underneath the existing one for sda5 and when you are done remove all the comment marks '#' at the beginning of the line. These simply mean the line is ignored. When you remove the # it means the line is 'in play' so to speak. 

Good luck with it and let us know how you went.

---

### Post by Jaraxle on 2009-10-13
I was just checking out the new version of Xubuntu, it was just temporary. That's why I didn't want to load Xfce in Ubuntu.

Ultimately what I did was delete the partition for Xubuntu (after reinstalling Grub to my Ubuntu partition), then install Linux Mint using the free space. I allowed Linux Mint to install Grub to the new partion and then edited menu.lst so that Ubuntu would be my default boot option instead of Linux Mint.

This time, it was straightforward. I'm guessing that the issues I was having with menu.lst before had something to do with the savedefault option. As in, it was using that option instead of the "default =" option, if that makes any sense. I'm also not sure because I don't fully understand how that option works.

Thanks for helping me! I'm glad that I'm learning Grub. I still don't understand some of the advanced features, but I'm getting there!

---

