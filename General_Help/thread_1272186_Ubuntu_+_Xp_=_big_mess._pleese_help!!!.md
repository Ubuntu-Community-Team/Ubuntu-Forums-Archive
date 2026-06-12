---
title: "Ubuntu + Xp = big mess. pleese help!!!"
date: 2009-09-21
forum: General Help
---

### Post by ubuntnoob512 on 2009-09-21
**[COLOR=Red]Please help[/COLOR]. Windows XP wont boot after installing Ubuntu.**


I have a very special computer. Here is it's lifestory. Ok so, i bought it off of ebay as a 2.2gz Core 2 Duo (pretty fast), a 512 NVIDIA graphics card that i was told was relly good, It has a 15.4 inch screen (laptop), Mainly MSI brand whitebox, 111 gb HD, 4 gb of ram, and Windows XP 64 bit (one of the worst operating systems ever. My computer would freze and i would have to restart often.

The computer with powercord, drivers, and actuall win XP 64 bit disk was about $325. Yes, a great deal.

From there I installed Vista 32 bit, vista 64 bit, windows home 32 bit, and finally windows pro 32 bit.

I just recently have put Ubuntu 8.04 on my Xp 32 bit computer. I Partitioned the drive already so i had 5 GB for Testing operating systems like Ubuntu and in the future i want to try snow leopard, Google chrome, other versions of linix, and windows 7. 

In the Ubuntu set up, it would only let me put windows and Ubuntu on the same partion so i currently have a blank 5 GB partion.

Well the who point of this posting:

when i turn on my computer, it goes to the screen that lets me choose between the 2 operating systems.

If i click in Linix, it boots just fine and i am using linix as I am posting this question.

If i click on Windows Xp pro, i get the same blue screen that says something like:
If this is the first time you have seen this screen, restart your computer

If you have seen this screen before, uninstall all newly installed programs. (yes the blue screen of death)

The only newly installed program is Ubuntu.

So, What do i do. I know some about computers but this is my first time using linix. I am not quite sure what to do. If you have read this whole thing and answered i thank you.
                                                      

                                     I forgot to say, I am 14, bad at spelling and i have the Actual Ubuntu disk and windows xp 32 bit on a disk and on a flash drive with a bunch of other stuff. ( i burned it)

               

 Linix is on the same partion as windows. And believe me, Windows can throw lots of hissy fits so i get those versions removed.

when I open Partion Editor it has something like this:

Partition _ File System ____Mount Point___ Label _ Size____ Used __ Unused _Flags 
  /dev/sda1     ntfs_____________            /media/disk_________                 104.41GB_70GB_34.41GB__boot
/dev/sda3      extended _______________________________2.5GB_____       ---____          ----        
/dev/sda5 ext3 / ________________________________ 2.33GB ___ 2.11GB_ 228MB 
/dev/sda6     linix-swap ____________________________172.54MB___  ----____         ----      
/dev/sda2     ntfs__________________________                                   Test Drive_4.88GB ___    ---- ____---    

some problems i need fixed:

i dont know how to install stuff on linix like flash players. How do i do that?

As you can see above... i have lots of partions. I want only one that I can put windows and ubuntu on. If it cant be done I can settle for two partions (one 85 gb and one 26 gb partion). 

All this needs to be done in linix:
How do I remove the partions?
How do I make the new partion?
How do I dual boot windows and linix once that is done?

And one more thing. When I launch firefox, and go to a high
javascript page, i have about 3 seconds until firefox just stopps working.

Is this just a bug?




so please help, i need it. And talk in English because I am only 14 and new to linix.:confused:

---

### Post by lisati on 2009-09-21
It almost sounds as if XP has gotten itsself totally confused. Short of reinstalling XP (which is likely to require you to reinstall "grub", one of the things that lets you choose which OS) I'm not sure what to suggest.

---

### Post by ubuntnoob512 on 2009-09-21
Ok, when i stick the disk into my computer, I try to boot from it, and it says:
 BOOT ERROR 
press any key to continue.

and when i press a key it says the same thing

and the same cycle continues.

---

### Post by Whiffle on 2009-09-21
In linux, go to Applications > Accessories > Terminal

and then run:

```

sudo fdisk -l

```

and 

```

cat /boot/grub/menu.lst

```

and then post up whatever it spits out here (shift + ctrl +c) to copy out of the terminal.  I'm trying to get a bearing on what your hard drive looks like.

With the BOOT ERROR, is that coming up from the BIOS, or is that from grub, the linux bootloader?

---

### Post by ubuntnoob512 on 2009-09-21
aaron@aaron-laptop:~$ sudo fdisk -l
[sudo] password for aaron: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe5cfe5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13630   109482943+   7  HPFS/NTFS
/dev/sda2           13957       14593     5116702+  83  Linux
/dev/sda3           13631       13956     2618595    5  Extended
/dev/sda5           13631       13934     2441848+  83  Linux
/dev/sda6           13935       13956      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
aaron@aaron-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=9001de93-af03-46da-9bb6-4ed07c6bf342 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9001de93-af03-46da-9bb6-4ed07c6bf342

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        9001de93-af03-46da-9bb6-4ed07c6bf342
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9001de93-af03-46da-9bb6-4ed07c6bf342 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        9001de93-af03-46da-9bb6-4ed07c6bf342
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=9001de93-af03-46da-9bb6-4ed07c6bf342 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        9001de93-af03-46da-9bb6-4ed07c6bf342
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by ubuntnoob512 on 2009-09-21
Oh, and that is when my computer starts up, before i select to start ubuntu, there is a screen that tells me to press f11 and blah blah blah

so it is probably the BIOS

---

### Post by Whiffle on 2009-09-21
Okie dokey.  I think this might apply to your windows problem:
[http://xibex.blogspot.com/2009/03/fix-blue-screen-error-eg.html](http://xibex.blogspot.com/2009/03/fix-blue-screen-error-eg.html)

But it looks like that will remove grub, so you'd no longer be able to get into Ubuntu.  You'll have to get a copy of the Ubuntu Alternate install CD, and then use the "rescue a broken system" option to reinstall grub.  However, that didn't seem to work too well the first time when it was installed to your MBR, so I would suggest installing grub to your /dev/sda5 partition, and then use the windows bootloader as described here: [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/3443-dual-booting-windows.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/3443-dual-booting-windows.html)

---

### Post by ubuntnoob512 on 2009-09-21
Ok, i will deal with that in the morning. I am gunna go 2 bed. My main mission isnt to fix windows and linix but to like re do everything on my computer. like clear the hardrive, and dual boot linix and windows. 

thanks for the help

i will need more in the morning.

no school tomarrow yay

because of flooding

our basement is flooded :'( :-\"

bye 4 now

---

### Post by Whiffle on 2009-09-21
Oh in that case, you should be able to arrange your hard drive however you like with the ubuntu install cd :)

Good luck with the basement.  Don't forget the pool toys :D

---

### Post by ubuntnoob512 on 2009-09-22
thanks, lol

the creek stopped flooding and we cleared out the wet carpet and stuff.

but how do i clear out the hard drive, do i just stick the cd in and it gives me some choces. i will try that.

---

### Post by ubuntnoob512 on 2009-09-22
well, that was esyer than i expected. I now have a 100% ubuntu hard drive.
 
now to install windows xp
 
how in the world do i double boot the 2?

---

### Post by Darkwing-Duck on 2009-09-22
Hey bro. You will want to partition a section of your hard drive to NTFS to boot windows on. Once windows is installed you will need to restore GRUB. Here is a good guide for restoring GRUB.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope is works out for ya!

---

### Post by ubuntnoob512 on 2009-09-23
ya, i am past that step on a newer thread:

[http://ubuntuforums.org/showthread.php?p=7994978&posted=1#post7994978](http://ubuntuforums.org/showthread.php?p=7994978&posted=1#post7994978)

---

