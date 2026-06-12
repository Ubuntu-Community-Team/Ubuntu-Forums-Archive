---
title: "Can I chainload wubi from grub?"
date: 2009-07-07
forum: General Help
---

### Post by bernied on 2009-07-07
I would like to be able to start my wubi install from grub on a usb stick, instead of from windows ntldr.

I have wubi successfully installed (posting this from it) on a laptop inside an NTFS partition.
I don't have the option of repartitioning or adding another disk on this machine, so this is the best way to run linux for me.
I want to get rid of all the wubi and ubuntu files in the root directory of the NTFS filesystem, delete the ubuntu entry from boot.ini, and preferably just have the root.disk and swap.disk images left, but put elsewhere.
I have a bootable usb stick with multiple partitions and lots of useful linux stuff on it, like a gparted 'live-cd' and slax, and these are all booted from grub.

So can anyone please tell me how to load wubildr from grub? Do I just need to put the wubildr.mbr into the the mbr of one of the usb stick partitions, then chainload it? I'm guessing I could do this with dd

Or can grub start wubi directly? Is grub able to work with NTFS?

I found some howtos for making a live-cd, and another for a bootable usb stick, but it uses isolinux, and I don't know how to make isolinux play with grub.

All ideas, or pointers, appreciated.

Thanks
Bernie

---

### Post by bernied on 2009-07-07
OK, so the answer might be [here](http://ubuntuforums.org/showthread.php?t=946356)
I've run grubinst on the usb stick partition, but it seems to have destroyed the filesystem on that partition, so I can't access it.
Maybe grubinst can only be run on the whole device mbr, not on a partition.
Must do some reading - tomorrow.

---

### Post by bernied on 2009-07-08
I know I'm just talking to myself here, but someone might find this useful, as I've found other monologue threads useful.

So it looks like wubi uses grub4dos to load - brilliant.
And there is documentation on grub4dos - [here](http://grub4dos.sourceforge.net/wiki/index.php/Grub4dos_tutorial)

[quote="The FM"]Loading GRUB for DOS using other boot loader

grub.exe can be loaded as a linux kernel.

Load GRUB for DOS using GRUB or another copy of GRUB for DOS, add the following section to menu.lst:

   title Load GRUB4DOS
   kernel /grub.exe[/quote]So as long as the wubi boot files come with a grub.exe, which I think I saw, then I don't have to install grub to a partition boot area at all, just get the relevant files there.

But the machine is at home, and I'm not, so it will have to wait until tonight to try out.

---

### Post by bernied on 2009-07-08
The answer to this seems fairly simple. Here's what I've done so far:
- installed wubi using the windows installer
- copied files in /host/ubuntu/winboot to a spare partition on my grub-bootable usb stick (in my case the 7th partition). It probably doesn't need its own partition, but it gets one anyway.
- added an entry to the grub menu.lst on the stick, like this:
```
title wubi
root (hd0,6)
kernel /wubildr.exe
```

And it works!

It looks like changing the default location of the /ubuntu directory is a bit more complicated. I will need to:
- make a copy of the /ubuntu folder to somewhere else, 
- modify the menu.lst in my usb partition to find the copy
- modify menu.lst in /ubuntu/disks/boot/grub
- modify fstab in the wubi install

Then I can uninstall the original, and pretend it never happened.

I'm a bit confused by this in the wubi install menu.lst:
```
root ()/ubuntu/disks
```
How does it know to look in the ntfs partition??
This must be something peculiar to grub4dos, because I don't think grub would like it.

---

### Post by flugh on 2009-07-08
I haven't used wubi before, so can add nothing in the way of advice. But I do appreciate you posting your findings here. Makes for a good read, and something to file away for future 'just in case' kind of stuff :)

---

### Post by bernied on 2009-07-08
All done now, tho the disk image might get moved again and renamed.

All other linux-related files have been moved off the ntfs partition, and boot.ini returned to its former simplicity.

The boot sequence is something like this:
- grub on the usb stick boot partition (5) boots first
- the wubi entry (as posted above) boots grub4dos, which is in the / directory on another partition (7) on the usb stick
- this then loads the last menu.lst file (using configfile), which is on the same partition (7), but in a directory called boot.
- this loads the standard kernel and initrd, and the kernel is then booted

That /boot directory in partition 7 of the usb stick is mounted at boot via fstab, so that it looks like a normal boot directory for the purposes of kernel updates etc.

---

