---
title: "Installing OS from within Ubuntu"
date: 2009-07-26
forum: General Help
---

### Post by audrich on 2009-07-26
I would like to know how to install an OS (preferably Windows XP) on an external HDD accessed by Ubuntu.  

Here's my dilemma: I have two laptops, one running Ubuntu that is wonderful and great, and another laptop with no OS that I want to put Windows XP on because Wine does not work for the Windows specific program I need.  The catch is, this laptop (Toshiba Portege M200) does not have an internal CDROM, and is very picky about what external CDROMs and USB flashdrives it will boot from.  So installing XP from CD or flash drive does not work (I've tried several times).

The only options left to me are:

1) Network install XP on to the pesky laptop.  There are several tutorials of how to do this from a Windows machine, but not one running a Linux.  I'm also not partial to networking so...

2) Put the pesky laptop's HDD in a USB enclosure (got one) and access it as an external HDD from my Ubuntu machine.  I'd like to install Windows on to it from Ubuntu, then put it back in to the other laptop as its primary internal HDD.  It sounds like the best solution, but when I try to do "wine setup.exe" on the XP setup disc, nothing happens...so is this option possible?

Note:
-I'm NOT looking to install Windows on the same HDD running Ubuntu
-I'm NOT trying to boot XP from an external drive (it'll run as an internal once the OS is on there)
-I canNOT simply use a CD or flash drive boot to start installer.

Any solutions guys?  Thanks.

---

### Post by Teabicky on 2009-07-26
I am no expert but I would have thought that you should be able to configure your bios to boot from most (if not all) external cdrom drives, here's a link that may help (sorry if i'm teaching you to suck eggs).

[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

Also, this looks of interest...

[http://www.velocityreviews.com/forums/t230863-cant-install-windows-xp-from-boot-on-toshiba-s1900102.html](http://www.velocityreviews.com/forums/t230863-cant-install-windows-xp-from-boot-on-toshiba-s1900102.html)

---

### Post by markharding557 on 2009-07-26
have you looked at virtualbox?
in this you can keep xp in a folder on your hd and yet be able to load it up any time in ubuntu

---

### Post by audrich on 2009-07-26
> **markharding557 said:**
> have you looked at virtualbox?
in this you can keep xp in a folder on your hd and yet be able to load it up any time in ubuntu

Putting XP on my Ubuntu machine is going to be my last resort, but I'd rather not have a perfectly good laptop lying around with no OS.  I'll put Ubuntu on that if I can't put Windows on it.

---

### Post by audrich on 2009-07-26
> **Teabicky said:**
> [http://www.velocityreviews.com/forums/t230863-cant-install-windows-xp-from-boot-on-toshiba-s1900102.html](http://www.velocityreviews.com/forums/t230863-cant-install-windows-xp-from-boot-on-toshiba-s1900102.html)

Tea, I followed one of the recommendations, placing the I386 folder contents on to the first partition, and placed it back inside the laptop hoping to boot from partition 1 and install on partition 2.

First I tried to make the first partition FAT16, but when I did this it could not copy all the files over.  I know there was plenty of space, but I think one of XP's file's name was too long for FAT16.

So then I made a FAT32 partition instead, everything copied over fine.  When I placed it back inside the laptop and turned it on, I get "Insert system disk in drive.  Press any key when ready..."  Press a key, just tries booting external devices (of course it fails) then gets back to the HDD and gives me the same message over.

What am I doing wrong?

---

### Post by ecol on 2009-07-27
I agree with Teabicky: it should be possible to configure the BIOS on your "empty" laptop so that it can boot from an external CD drive. However, if you want to put your spare HDD in an external housing and install Windows, this is how I would do it:

[LIST=1]
[*]Put the HDD in the external housing and attach it to any old computer that you can boot from CD.
[*]Boot the computer from the Windows install CD.
[*]When you get to the Windows partition editor stage, select the external HDD as the Windows C drive. Be careful not to accidentally install over the computer's internal HDD.
[/LIST]
I haven't tested this approach with Windows, but I have used it to install various Linux distributions in the past.

---

### Post by egalvan on 2009-07-27
> **audrich said:**
>  placing the I386 folder contents on to the first partition, placed it inside the laptop hoping to boot from partition 1 and install on partition 2.

I made a FAT32 partition instead, everything copied over fine.  When I placed it back inside the laptop and turned it on, I get **"Insert system disk in drive.  Press any key when ready..."**  Press a key, just tries booting external devices (of course it fails) then gets back to the HDD and gives me the same message over.

What am I doing wrong?

That error means that there is no boot system on the drive.

does your lappie have a floppy?

If so, then put the hard drive in another computer, then create & format a NTFS partition, making it 1GB less than the full disk.
The remaining 1Gb is made into a FAT32 partition.
Copy EVERYthing on the XP install cd to this 1gb partition.

Replace hard drive in original lappie,
boot from a Win98 floppy, navigate to the 1gb partition, and fire up "setup.exe"....
(N.B. this may be called "install.exe" or similiar... it will be in the root of the CD)

you can try "setup.exe /help" to see if there are any run-time commands available.


Remember that XP really really wants to be the first partition on the first hard drive...it gets very unhappy if it doesn't get it's way (work-arounds exist)


As  for your lappie being "picky" about what it  will boot off the USB, have you checked on any available BIOS updates?

Some older BIOS/chipset combos will not boot (or see) any flash larger than 2GB.
Some will not boot from CD/DVD drives, only CD.


And further, if you install XP on another machine, then try to transfer the drive to your original machine,
chances are high that it will have problems.

Chipset, IDE drivers and video drivers will give problems.
XP hard-codes the drivers during install.
Unless the hardware is basically identical, you will have problems.

Not to forget that you will have to 'REACTIVATE' the install,
due to the changes in the hardware.

---

### Post by audrich on 2009-07-27
> **ecol said:**
> I agree with Teabicky: it should be possible to configure the BIOS on your "empty" laptop so that it can boot from an external CD drive. However, if you want to put your spare HDD in an external housing and install Windows, this is how I would do it:

[LIST=1]
[*]Put the HDD in the external housing and attach it to any old computer that you can boot from CD.
[*]Boot the computer from the Windows install CD.
[*]When you get to the Windows partition editor stage, select the external HDD as the Windows C drive. Be careful not to accidentally install over the computer's internal HDD.
[/LIST]
I haven't tested this approach with Windows, but I have used it to install various Linux distributions in the past.

Tried this, but when I got to choosing the correct external partition to install, it said it could not access it even though it saw it when it gave me the options.  I'm going to guess this is a BIOS problem with the host computer because it did not list the external in the boot menu.

---

### Post by audrich on 2009-07-27
> **egalvan said:**
> That error means that there is no boot system on the drive.

does your lappie have a floppy?



Unfortunately no.  I did try copying all the files to a seperate partition like you said, the problem of course is there is no OS (like DOS) to run the set up.  I tried copying the MSDOS floppy files directly to the partition, hoping it will boot from that, but it didn't like it one bit.

You bring up a good point though about XP hardcoding the chipsets et al and then flipping its lid when it gets transfered over to the intended hardware.  Oy what a headache.

---

### Post by moster on 2009-07-27
XP do not support standard installation from usb but vista and windows 7 do. If you have newer laptop from 2005+ that support boot from USB and with special format of usb you can install it, from Ubuntu.

If you just copy winxp files or vista on usb of course it was not run setup :)

---

### Post by audrich on 2009-07-27
> **moster said:**
> XP do not support standard installation from usb but vista and windows 7 do. If you have newer laptop from 2005+ that support boot from USB and with special format of usb you can install it.

If you just copy winxp files or vista on usb of course it was not run setup :)

I placed it back inside the intended laptop once I copied the files to it as an external, so it shouldn't try to boot from USB.  It cannot boot XP or DOS when either is on the internal drive.  I figured that would happen with XP but not with MSDOS.

---

### Post by Taus on 2009-07-27
hmm weird that it wont boot from USB...
I have the Portege R500 and it boots fine from my Kingston datatraveler 4gb usb pen.

a while back i even installed xp from a usb pen. not because i needed to but just for trying if it was possible.

---

### Post by moster on 2009-07-27
Sorry, I just do not understand you. Without USB or DVD-rom boot you cannot install any OS. It leave you just to wish you luck. bye :)

---

### Post by audrich on 2009-07-28
> **moster said:**
> Sorry, I just do not understand you. Without USB or DVD-rom boot you cannot install any OS. It leave you just to wish you luck. bye :)

I'll try to break it down easier:

I have two computers, let's call them Wendy and Bento.  Wendy has no OS, no internal CDROM drive, and for all practical purposes, does not boot from any external device (unless I want to find/buy one of the few it does).

I want to take out Wendy's HDD, set it up as an external HDD, and hook it up to Bento, who runs Ubuntu.  Somehow, I will put Windows on this external HDD (call it Wendy's brain in a jar), then when I'm done, transplant it back into Wendy.

A further problem is that although Bento can boot from external devices, and see Wendy's brain in a jar, it cannot write to it when booting XP install CD.  It can tinker with it just fine from Ubuntu, and it can see it in boot mode, but not write to it...

---

### Post by moster on 2009-07-28
I now understand. :)
Ok, you have two possible solutions.

1. This option is not sure how it actually works, but it is possible because I have it on my Eeepc. In basic, ih has some hidden partition where is windows installation. It starts when I first turn on computer. It has some name.. some backup something... I will get back to you with details, I will have more time in few hours.

2. Take HDD from that computer put it in another, install windows and put it back. Of course thi is not 100% sure but I pull that one. I took HDD from fully installed AMD machine, put it in intel and WINXP boot to desktop.

---

### Post by jocko on 2009-07-28
> **audrich said:**
> I'll try to break it down easier:

I have two computers, let's call them Wendy and Bento.  Wendy has no OS, no internal CDROM drive, and for all practical purposes, does not boot from any external device (unless I want to find/buy one of the few it does).

I want to take out Wendy's HDD, set it up as an external HDD, and hook it up to Bento, who runs Ubuntu.  Somehow, I will put Windows on this external HDD (call it Wendy's brain in a jar), then when I'm done, transplant it back into Wendy.

A further problem is that although Bento can boot from external devices, and see Wendy's brain in a jar, it cannot write to it when booting XP install CD.  It can tinker with it just fine from Ubuntu, and it can see it in boot mode, but not write to it...
If you install windows on the hard drive when it's connected to one computer, and then move the hard drive to another computer, windows will most likely fail to boot because all the hardware is different. But it may be possible to come around that by creating hardware profiles, so you can tell windows to detect new hardware before it boots...

You can't just copy windows or dos files to a hard drive and think it will become a bootable drive. You have to install a boot loader into the mbr of the drive, and tell the boot loader where to look for an operating system. If you don't, you will just get a bios error saying you have no bootable devices.

It's probably possible to install dos (maybe from a win98 diskette?) or freedos to a small partition on the drive when it's connected to the other computer, then move the hard drive to the correct computer, boot dos/freedos and install windows from there...
But I'm not sure how to do it, just that you probably need one small fat32 partition for dos/freedos, and you can probably copy the i386 folder from the windows cd to this partition once dos/freedos is installed.

---

### Post by egalvan on 2009-07-31
> **audrich said:**
> I'll try to break it down easier:

I have two computers, let's call them Wendy and Bento.  Wendy has no OS, no internal CDROM drive, and for all practical purposes, does not boot from any external device (unless I want to find/buy one of the few it does).


It breaks down like this...

You need to install a boot loader on that drive...
SuperGRUB can do this.
It can install a bog-standard IPL on the MBR of the drive.

You need to install a minimal OS, one that will boot,
allows you to traverse drives/directories,
and launch an .exe type program.
DOS will do this.

I used to do this, hooking up the empty hard drive to the IDE cable...
booting from a DOS floppy,
and formating the hard drive with the FULL FORMAT and COPY SYSTEM FILES
options.


OK, so we know Wendy cannot boot from anything other than the hard drive.

What about Bento?
What boot options are available for it?

Floppy?
CD?
DVD?
Hard drive?
USB?

---

