---
title: "Just effectively reinstalled Windows. How do I restore GRUB with the Dapper LiveCD?"
date: 2006-06-24
forum: General Help
---

### Post by AirRaven on 2006-06-24
My setup until now has been two seperate hard discs, with Windows XP on the master (hda), and Ubuntu Dapper on the Slave (hdb). I've just cloned my XP install and transferred it to a new HD, which has taken the place of the old "master" HD.  

This works perfectly well, so long as I want to simply boot into Windows with no possibility of accessing Linux without a Boot CD.

How can I restore GRUB? I'm currently on the Dapper Drake Live/Install CD.

I've tried [FONT="Lucida Console"]sudo grub-install hdb[/FONT], but it gives me this:
```
ubuntu@ubuntu:~$ sudo grub-install hdb
Format of install_device not recognized.
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-shell=FILE       use FILE as the grub shell
  --no-floppy             do not probe any floppy drive
  --force-lba             force GRUB to use LBA mode even for a buggy
                          BIOS
  --recheck               probe a device map even if it already exists

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into the DIR/boot directory specfied by
--root-directory, and uses the grub shell to install grub into the boot
sector.

Report bugs to <bug-grub@gnu.org>.

```

I'm sure it's a problem with my syntax. I just have no clue how to use this command.

---

### Post by aysiu on 2006-06-24
Try [this](http://ubuntuforums.org/showpost.php?p=117829&postcount=2).

---

### Post by tonyr on 2006-06-24
...and here's an extended treatment...
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by AirRaven on 2006-06-24
Slight problem with the linked methods- I tried setting up GRUB on (hd1,0), and it seemed to work fine in the terminal.

When I rebooted, Windows still hijacked the boot process as normal and started up.

Am I meant to use my Windows NTFS HD as the root, or my Ubuntu HD Partition?

Either doesn't seem to work.

---

### Post by Ramses de Norre on 2006-06-24
The root is your ubuntu partition (the one containing /boot), but you have to give the hard disk you boot from as argument with setup.

---

### Post by AirRaven on 2006-06-24
[QUOTE=Ramses de Norre]The root is your ubuntu partition (the one containing /boot), but you have to give the hard disk you boot from as argument with setup.[/QUOTE]
Whoops- my bad. I was stating (hd0,1) in "setup" rather than just (hd0). Works perfectly now- many thanks. :)

---

### Post by AirRaven on 2006-06-24
...Perhaps not.

Ironically, I can now access Ubuntu perfectly well, but Windows XP Professional refuses to boot. 

I select Windows XP in the GRUB menu, and it simply prints a message along the lines of "Entering GRUB stage2", and then returns to the menu.

I have a feeling I've just removed Windows' bootloader completely. I assume that GRUB normally forwards the booting to NTLDR when you select to boot from Windows normally?

Is there any fix for this that will leave GRUB intact? I'm not sure whether I should try "fixmbr" or "fixboot" in the Windows Recovery Console or not.

---

### Post by tonyr on 2006-06-24
[QUOTE=AirRaven]
I have a feeling I've just removed Windows' bootloader completely. I assume that GRUB normally forwards the booting to NTLDR when you select to boot from Windows normally?

Is there any fix for this that will leave GRUB intact? I'm not sure whether I should try "fixmbr" or "fixboot" in the Windows Recovery Console or not.[/QUOTE]

It's the other way round, actually: The GRUB bootloader forwards the boot process
to Windows.   Post your **/boot/grub/menu.lst** here and let's have a look.

You can use **fixmbr**, but the result is that you will end up with only a Windows
boot.  That might not be such a bad thing: at least it will get you back to a known
place.

I haven't ever tried scattering bootloaders around to different partitions/drives.  I stick
with a bootloader on /dev/hda and arrange for the configuration files **menu.lst** or
**lilo.conf** to know where boot images are, drive- and partition-wise.

---

### Post by AirRaven on 2006-06-24
[QUOTE=tonyr]It's the other way round, actually: The GRUB bootloader forwards the boot process
to Windows.   Post your **/boot/grub/menu.lst** here and let's have a look.[/quote]
Here you go:

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
default		4

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

title		Ubuntu Linux 6.06
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-k7 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-k7 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-k7 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-25-k7
boot

title		MemTest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```


[quote=tonyr]You can use **fixmbr**, but the result is that you will end up with only a Windows
boot.  That might not be such a bad thing: at least it will get you back to a known place.[/QUOTE]
Part of the reason I'm so eager to get back to Windows is so that I can use PartitionMagic to clone my existing Ubuntu partition to the old Windows HD so I can have more than 10GB of space to play with- the current situation's a little limiting in what I can do.

---

### Post by tonyr on 2006-06-24
This is a guess.  In that final entry:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

change **(hd0,1)** to **(hd0,0)**.  Notice that the comment says non-linux OS on **/dev/hda2**.
I'm guessing that your Windows OS is on **/dev/hda1**

---

### Post by AirRaven on 2006-06-24
[QUOTE=tonyr]This is a guess.  In that final entry:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

change **(hd0,1)** to **(hd0,0)**.  Notice that the comment says non-linux OS on **/dev/hda2**.
I'm guessing that your Windows OS is on **/dev/hda1**[/QUOTE]
No luck.

I think I've actually overwritten Windows' boot sector completely. I'm going to try FixMBR and try to solve it from within Windows. I must have used the wrong setting somewhere.

---

### Post by dmartinsca on 2006-06-24
Also, it may not be necessary but I have always used **rootnoverify** instead of **root** when booting windows from grub.

---

### Post by AirRaven on 2006-06-24
...Okay. I'm now inclined to be of the opinion that this was a *staggeringly* bad idea.

[img]http://img99.imageshack.us/img99/8254/picture123rz.jpg[/img]

NTLDR no longer exists, as you can see. "fixmbr" and "fixboot" do nothing whatsoever.

I know this is an Ubuntu support forum, but is there any way of replacing NTLDR? I've just installed GRUB on the MBR, removing NTLDR. I just want GRUB to be able to load Windows.

If all else fails, I can always backup what I can onto a DVD or two then reinstall, but the thought of waiting for Anarchy Online, Steam, and PlanetSide to redownload, not to mention the reams of Windows Updates and the hastle of waiting for Automatix to get what it needs doesn't quite appeal to me.

---

### Post by tonyr on 2006-06-24
Just as a sanity check, is your Windows still there, does Ubuntu see the partition and mount
it?  I'm pretty sure this is all just a bookkeeping snag, and things are not being searched for
in the right places.

If the partition is there and can be mounted, see if it looks anything like this (from
my XP, yours will be a little different):
> 
total 721525
dr-x------ 1 root root         0 2004-09-24 20:16 1bb7009b8642325d4e1a60d6
dr-x------ 1 root root         0 2004-09-24 20:40 a7f6d4f6b39a282c284a4afa93129eed
-r-------- 1 root root         0 2002-09-02 17:59 AUTOEXEC.BAT
-r-------- 1 root root       211 2004-09-25 10:01 BOOT.INI
-r-------- 1 root root       512 2002-09-02 17:38 BOOTSECT.DOS
-r-------- 1 root root         0 2002-09-02 17:59 CONFIG.SYS
dr-x------ 1 root root     12288 2005-11-19 23:54 DELL
-r-------- 1 root root      3800 2002-12-18 17:39 DELL.SDR
dr-x------ 1 root root      4096 2006-06-09 11:05 Documents and Settings
dr-x------ 1 root root      4096 2002-12-18 17:19 DRIVERS
dr-x------ 1 root root         0 2002-12-26 10:02 EPSON
-r-------- 1 root root 535875584 2006-06-23 15:12 hiberfil.sys
dr-x------ 1 root root   1208320 2002-12-25 19:08 I386
-r-------- 1 root root         0 2002-09-02 17:59 IO.SYS
-r-------- 1 root root       338 2002-12-18 18:17 IPH.PH
-r-------- 1 root root         0 2002-09-02 17:59 MSDOS.SYS
dr-x------ 1 root root         0 2005-12-29 11:49 My Downloads
dr-x------ 1 root root         0 2002-12-18 18:16 My Music
-r-------- 1 root root     47564 2004-09-25 09:34 NTDETECT.COM
-r-------- 1 root root    250032 2004-09-25 09:34 NTLDR
-r-------- 1 root root 201326592 2006-06-23 15:12 pagefile.sys
dr-x------ 1 root root     24576 2006-06-18 12:44 Program Files
dr-x------ 1 root root         0 2005-11-11 20:19 RECYCLER
dr-x------ 1 root root         0 2004-09-25 10:13 System Volume Information
dr-x------ 1 root root     77824 2006-06-23 15:15 WINDOWS


Notice that NTLDR is just a file.  From what I've read, NTDETECT.COM is a
necessary companion.  If either one of those is not there, you should be able to copy
it (them) from somewhere (ya gotta be root, though).

I'm gonna be unavailable for the next 12 hours or so.

---

### Post by dmartinsca on 2006-06-25
I really doubt that NTLDR is gone since it's just a file in the root of C:/
Could you post the output from **fdisk -l**, your menu.lst file if it has changed from before and the most recent grub commands you used to install it?

---

### Post by tammx on 2006-09-17
I have the same problem, I have Dapper Drake installed but am working now in Breezy Badger LiveCD because Windows overwrote my mbr.
However, 

grub> root (hd0,1)

Error 21: Selected disk does not exist

I get the same error with almost any value, hd0,0, hd 0,2 etc...
My old / is on /dev/hda2, windows is on /dev/hda1...
What am I missing?

EDIT: gaah I was missing sudo... no brain, no pain ](*,)

---

### Post by Herman on 2006-09-17
If it's any comfort, while you are trying to get Grub configured to boot Windows XP, you can always make your own NTLDR boot disk. 
I made a couple of them, they have boot.ini, NTLDR, and NTDETECT.COM on them. 
Here's the link, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/")
You need to format a floppy disk first, I had trouble getting mine to work until I did it exactly the way the howto specifies, from a Windows command line.

It is supposed to be able to boot your system even if NTLDR is really missing, but I doubt that very much too. You should be able to take a look and see them there, like this, [Click Here]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP"). Being able to boot from a floppy disk should make you feel better for now.

I hope that helps, Regards, Herman :D

---

