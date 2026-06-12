---
title: "Dual booting WinXP &amp; Ubuntu 9.04"
date: 2009-09-30
forum: General Help
---

### Post by lainmaster on 2009-09-30
Hey there, I'm new (both to the forums and Ubuntu), I'm trying to find my way with Ubuntu. Seems lovely up to know =)

But I got two problems which I can't seem to solve.
I didn't know whether to put them both in one thread or separate threads, I chose the latter. Hope I'm not breaking any rules...

Anyhow, 

I had Windows 7 and Windows XP. It was 3 partitions in one HD (two OS' and one for files) and another separate HD (which doesn't have any system, it's just media files and stuff). 
When booted, I used to get the Windows 7 screen, that allowed me to either boot 7 or XP.
I thought I had tested 7 enough and wanted to try Ubuntu, so I (from the Ubuntu CD which I downloaded and burned) deleted the 7 partition and made a 2GiB swap partition, and, what was left, an Ubuntu partition on which I installed it. (About 50 GiB)
Now when I boot I get an Ubuntu boot screen that shows several Ubuntu options and a WinXP option. Ubuntu works fine, but if I choose WinXP, I get
"Error 12: Invalid device requested".
I didn't  change anything more than what I said.
The details for the WinXP boot option seem to be:
rootnoverify (hd0,4)
savedefault
makeactive
chainloader++

What can I do to be able to boot WinXP again? (and also Ubuntu, whenever I want to). The only thing I can think of is using Windows XP CD's restore thing to restore the boot menu, but that would stop me from using Ubuntu...

I tried changing rootnoverify (hd0,4) to rootnoverify (hd0,2); that gives me "Starting up.../NTLDR is missing".

Any help?

---

### Post by QIII on 2009-09-30
Could you go to the terminal and paste the results of 

```
fdisk -l
```

That's a small "ell" not a "one".

---

### Post by Commander_Keen on 2009-09-30
Is there any data that you need from XP?

---

### Post by Giblet5 on 2009-09-30
> **QIII said:**
> Could you go to the terminal and paste the results of 

```
fdisk -l
```

That's a small "ell" not a "one".


I think that needs to be ```
sudo fdisk -l
``` and I'd get the output of ```
df
``` as well, just in case /boot is on another filesystem.

That will display all of the disk partitions on your computer and what type they are. It's very easy to set up a boot menu once you have that information.

---

### Post by QIII on 2009-09-30
Yes, sudo.

Oversight.  Thanks for pointing that out.

---

### Post by lainmaster on 2009-09-30
This is the output for  ```
sudo fdisk -l
```
```
isk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x004a004a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       16603   133355565    f  W95 Ext'd (LBA)
/dev/sda3   *       16604       38914   179200000    7  HPFS/NTFS
/dev/sda5               2       10199    81915403+   7  HPFS/NTFS
/dev/sda6           10200       10442     1951866   82  Linux swap / Solaris
/dev/sda7           10443       16603    49488201   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4e4a2a94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   42  SFS

```

---

### Post by QIII on 2009-09-30
Just noticed something about your menu.lst.

You should be looking at sda3 (zero based, so (hd0,2) as you tried.

But your C&P has "chainloader ++".  That should be "chainloader +1"

Try:

rootnoverify (hd0,2)
savedefault
makeactive
chainloader +1

If that doesn't work, post the entire contents of menu.lst.

---

### Post by lainmaster on 2009-09-30
I think it actually has chainloader +1, I don't know why I wrote ++. I think I copied it to paper first and then wrote it here from the paper, and got it wrong. Anyhow, I tried both 2 and 4, and even tried all from 0 to 9 and also the other hard drive, and chainloader is +1. Noone worked. I'm guessing this isn't an issue with the bootloader thing, but rather, a problem with the partitions. The NTDLR file or whatever isn't really missing, but I get that message if I try with 2. Any ideas?
By the way, if I go to console mode by pressing c and write those commands manually, when I write savedefault, it tells me that that command doesn't exist or something like that. "savedefault" is in the list that appears when I press tab, but it isn't in the one that shows when I write "help". Oddly enought, if i write help savedefault, I do get help for that command. Anyway, if I skip that command, it seems that "makeactive" is the one generating the error. (The invalid device one, I don't get this with hd0,2; in that case, I still get the missing NTDLR or whatever).

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
# kopt=root=UUID=34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        34e9c2dc-fa64-4fb4-b2fa-fa0305d2e969
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title        Windows NT/2000/XP
rootnoverify    (hd0,4)
savedefault
makeactive
chainloader    +1
```It says rootnoverify    (hd0,4) but I also tried rootnoverify    (hd0,2) and many others by editing on the fly.

In case it's relevant: I first installed Windows XP, then Windows 7, that was what I had until some days ago, when I deleted Windows 7's partition and put Ubuntu (explained in my first post in this thread).

---

### Post by oldfred on 2009-09-30
Windows installs to both the MBR and to the boot sector within the partition. This is why Grub works chainbooting as it points to the boot within the partition. 
Windows 7 somehow consolidates the boot into 1 and gives you a menu to choose. When you deleted the Win7 partition you lost the boot. 

I do not know if there is a better way but you probably have to repair your XP install which will probably overwrite the MBR, so you will have to reinstall that. 

I would try Supergrub first as it repairs lots of things and you might be able to do both fixes in one.
[http://www.supergrubdisk.org/w/index.php5?title=SuperGrubDisk](http://www.supergrubdisk.org/w/index.php5?title=SuperGrubDisk)

---

### Post by lainmaster on 2009-09-30
If I repair Windows XP, I can get the MBR back to working for XP, but I'll lose it for Ubuntu.
From there, what should I do to get GRUB working for both Ubuntu and Windows XP?

---

### Post by arrange on 2009-09-30
There is a problem with your Windows installation being on a logical partition, not a primary one I guess. I would try to set the boot flag to *sda5* (i.e., (hd0,4)), and comment out the *makeactive* command in the *menu.lst* file.

---

### Post by AlexsAntidote on 2009-09-30
I had a similar problem once... I had Vista and XP (in that order) and then decided to delete the Vista partition to install Ubuntu. Then I could boot into Ubuntu but not Windows (since I killed the MBR when I removed the Vista partition).

I recommend trying Supergrub and see if you can simply restore the Windows MBR. It should be able to repair any boot problems you may have. The help for Supergrub takes a bit if getting used to but it is quite helpful...

I think the site has changed a bit since I last downloaded it, but I believe the site is found here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Good luck!

---

### Post by woohoo576 on 2009-09-30
I've used ubuntu for about a year now. Being only 13 I can't buy a copy of XP so I'm stuck :(. If you get XP back, download wubi and it should create a dual boot. I think you can boot into XP and put in the ubuntu disc to do the same thing. Good luck!

---

### Post by lainmaster on 2009-09-30
> **arrange said:**
> There is a problem with your Windows installation being on a logical partition, not a primary one I guess. I would try to set the boot flag to *sda5* (i.e., (hd0,4)), and comment out the *makeactive* command in the *menu.lst* file.

Yes, I think that is the problem, although, I think I tried that already. Will try again now, just to check. 

EDIT
Tried that, got the following: "Starting up.../A disk read error ocurred/Press Ctrl+Atl+Del to restart". Oddly enought, Ctrl+Alt+Del didn't restart, had to hit the power button.
/EDIT

Also, I downloaded Super Grub thingy, but it seems it'll take a while before I figure out how to use it.

---

### Post by arrange on 2009-10-01
> **lainmaster said:**
> 
EDIT
Tried that, got the following: "Starting up.../A disk read error ocurred/Press Ctrl+Atl+Del to restart". Oddly enought, Ctrl+Alt+Del didn't restart, had to hit the power button.
/EDIT

I think this is a Windows message, so Grub managed to successfully chainload and now it's a Windows problem.

You may end up reorganizing the whole drive so that you are able to put your Windows installation on the first primary partition :(

---

### Post by lainmaster on 2009-10-01
By that you mean formatting and installing everything again? I hope not >_>

---

### Post by oldfred on 2009-10-01
If your window is in sda3 you should not have to reformat. If it is really in sda5 you may have to, although I have found several work arounds to allow a windows extended partition to boot (not easy). Windows only directly boots from a primary partition.
Your sda3 is a primary partition as I read your fdisk.
[FONT=monospace]/dev/sda1               2       16603   133355565    f  W95 Ext'd (LBA)
/dev/sda3   *       16604       38914   179200000    7  HPFS/NTFS
/dev/sda5               2       10199    81915403+   7  HPFS/NTFS
[/FONT]Your sda1 - extended is 2 thru 16603 where sda3 labeled boot with the * starts at 16604 so it is not in the extended partition.

This entry is trying to boot the sda5 which is extended. Change to sda3
[FONT=monospace]title        Windows NT/2000/XP
rootnoverify    (hd0,[COLOR=Red]4[/COLOR])
savedefault
makeactive
chainloader    +1[/FONT]

to make it sda3 change (hd0,4) to (hd0,2) and you should be able to boot the windows in sda3.

---

### Post by lainmaster on 2009-10-01
> **oldfred said:**
> If your window is in sda3 you should not have to reformat. If it is really in sda5 you may have to, although I have found several work arounds to allow a windows extended partition to boot (not easy). Windows only directly boots from a primary partition.
Your sda3 is a primary partition as I read your fdisk.
[FONT=monospace]/dev/sda1               2       16603   133355565    f  W95 Ext'd (LBA)
/dev/sda3   *       16604       38914   179200000    7  HPFS/NTFS
/dev/sda5               2       10199    81915403+   7  HPFS/NTFS
[/FONT]Your sda1 - extended is 2 thru 16603 where sda3 labeled boot with the * starts at 16604 so it is not in the extended partition.

This entry is trying to boot the sda5 which is extended. Change to sda3
[FONT=monospace]title        Windows NT/2000/XP
rootnoverify    (hd0,[COLOR=Red]4[/COLOR])
savedefault
makeactive
chainloader    +1[/FONT]

to make it sda3 change (hd0,4) to (hd0,2) and you should be able to boot the windows in sda3.
As I said before, I already tried both (hd0,4) and (hd0,2). With (hd0,4) I get the "Invalid device" error, with (hd0,2) I get the "NTLDR is missing" error.
Is that what you meant?

---

### Post by oldfred on 2009-10-01
Windows installs into the MBR and into the windows partition the MBR points to the partition to load windows. With Grub it takes over the MBR but still uses the NTLDR in the windows partition to chain boot into windows. if "NTLDR is missing" then the windows boot is missing in the partition.
Someone mentioned supergrub, it will solve your problem as it can fix older windows boot problems.

---

### Post by lainmaster on 2009-10-01
NTLDR can't be really missing, since I could boot normally when I had 7, and I manually checked that that file exists, too. As for SuperGrub, I don't really understand how to use it. I downloaded the CD version and recorded it, configured my BIOS to start up from the CD, and something different to the usual Grub, but very similar, showed up. It had options to boot windows and linux, but nothing else, and the windows options failed.+
EDIT
Oh, you mean that that error means that the Windows boot is missing in Windows' partition. I see. Well then, using Windows' recovery to restore its boot menu should fix the partition, and then I can use Ubuntu's CD to reinstall Grub, which should work, right?

---

### Post by oldfred on 2009-10-01
Supergrub may let your do it all at once. Win7 was the problem, It combines the partition boot into one and I guess it deletes the one in XP. It must assume you will not uninstall Win7 but will uninstall XP.

If supergrub cannot do it all (I have not tried) then you comment is correct, it is a two step process to correct the boot.

Supergrub will fix older windows boot problems and fix grub problems.

---

