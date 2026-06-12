---
title: "Is there a portable linux distro?"
date: 2009-11-20
forum: General Help
---

### Post by emigrant on 2009-11-20
hi all,
im wondering whether this is a portable linux distro which i can carry everywhere.
for example i can use it in my class instead of MS.
thank you all.

---

### Post by John Bean on 2009-11-20
Many (most?) recent distributions come in the form of "LiveCD" with the option to install. The LiveCD can if needed be put on a USB flash and is a completely self-contained portable OS.

---

### Post by emigrant on 2009-11-20
im looking for permanent use, ie. the saved documents should be still there if i plug in the pen/cd into another computer.
i don't think it is possible with the livecd.
also i should be able to update and install new apps to the system.

---

### Post by snowpine on 2009-11-20
You can install Ubuntu to a USB pen drive, just as you would to a regular computer. Then (assuming the computer has the capability to boot from USB), you can have a truly portable "Ubuntu on a stick".

---

### Post by emigrant on 2009-11-20
> **snowpine said:**
> You can install Ubuntu to a USB pen drive, just as you would to a regular computer. Then (assuming the computer has the capability to boot from USB), you can have a truly portable "Ubuntu on a stick".
i tried this a while back and ended up in damaging mbr/grub (not sure what) and had to reinstall ubuntu.
**if i take the pendrive and plug into another computer will it work?**

---

### Post by John Bean on 2009-11-20
> **emigrant said:**
> im looking for permanent use, ie. the saved documents should be still there if i plug in the pen/cd into another computer.
i don't think it is possible with the livecd.

Yes it is if you make a Ubuntu USB disk from a LiveCD using the "USB Startup Disk Creator". It creates a persistent installation and allows you to use the free space on the disk for data. I use one (Jaunty) all the time :-)

---

### Post by emigrant on 2009-11-20
i went to 'usb startup disk creater' from my current ubuntu, and it says, the tool is to modify essential startup things... :(

---

### Post by P4man on 2009-11-20
If your stick is big enough you can even do a normal installation on to the stick. It will take more diskspace but will boot a whole lot faster (and wear your stick out a lot faster too). You only have to take care that in the last step of the installation procedure you click on advanced and set the bootloader to install on the usb stick, rather than the first harddrive. If you want to be 100% sure not to mess things up, disconnect your harddrive, boot from a livecd and install on the thumbdrive.

A regular install will boot from just about any PC, only problem is videodrivers. If you install binary nvidia or ati drivers, it will probably fail to boot upon a machine with the other card. You can work around that with this little script I made:

[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

it will load nvidia drivers on machines with nvidia card and ati drivers for ati. Works on any machine Ive tried it on.

---

### Post by emigrant on 2009-11-20
how can i use the rest of the space while the format of the disk will be ext*?
it wont be detected in MS right?

---

### Post by P4man on 2009-11-20
> **emigrant said:**
> i went to 'usb startup disk creater' from my current ubuntu, and it says, the tool is to modify essential startup things... :(

Hu? You must have misclicked. But I would recommend you dont use USB startup creator anyhow, its bugged. Use unetbootin to make a livecd USB stick:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by P4man on 2009-11-20
> **emigrant said:**
> how can i use the rest of the space while the format of the disk will be ext*?
it wont be detected in MS right?

If you do a livecd install, then you can read the USB from windows, no problem. However, windows can not read the persistence file, so you must use use a persistence file that is smaller then your free space. what remains free can be read/written to by windows (and ubuntu)

If you do a full install, windows can not read anything on the drive. Not even if you make a separate partition because windows can not read multiple partitions on USB sticks.

---

### Post by fancypiper on 2009-11-20
I think there is a utility you can install in Windows that will let it read (if not write) ext3 file systems.  I haven't heard if ext4 is supported or not.

---

### Post by emigrant on 2009-11-20
My pen is 4gb so i thnk ubuntu is too much. How about puppy linux or an older version of ubuntu may be?

---

### Post by fluffman86 on 2009-11-20
You really don't want to do a full install on a USB stick unless you want to wait 10 minutes for it to boot, and another 5 for firefox to start.  It is SOOOO SLLOOOOOWWW.

Use Unetbootin or Sytsem > Administration > USB Start Disk Creator to install a Live CD, and create a persistence file to store all of your saved information.  This works REALLY well for me; I use it all the time.  

Pair it with the plop boot cd, and you're invincible! or...something else really awesome...

[http://www.plop.at/en/bootmanagerdl.html](http://www.plop.at/en/bootmanagerdl.html)

Get the file on top, extract, and look around for plbt.iso.  That will let you boot older computers with a CD, then the CD will boot from your USB.

Edit: I didn't explain WHY a standard install was slower.  When booting off of a USB drive with a full install, you're pushing something like 4GB into the computer.  When using a LiveUSB, you're pushing 700MB, then the computer is unpacking it.  Most of the time, your USB port is going to bottleneck way before your CPU.  In other words, your CPU can unpack 700MB faster than your USB drive can send 4GB unpacked.

---

### Post by Vakman on 2009-11-20
Try out Puppy Linux. Very light, if the computer has more than 512MB RAM then it will copy the OS to RAM so it will be very responsive. Many not as flashy as other distros but is beautiful for a portable OS. Hope this helps a little.

---

### Post by snowpine on 2009-11-20
> **emigrant said:**
> i tried this a while back and ended up in damaging mbr/grub (not sure what) and had to reinstall ubuntu.
**if i take the pendrive and plug into another computer will it work?**

As p4man mentioned, when you get to the last step of the installer, be sure to click Advanced Options and install GRUB on the USB stick (not your hard drive). Sorry I was not clear about this in my original post, it's been a while since I did it. I would also recommend choosing Manual partitioning and *not* installing a swap partition on the USB drive (it is not good for the longevity of the drive).

If you also want to use the drive for data in Windows, you need to partition it so that the *first* partition is a Windows format (like fat32). Windows can only see the first partition (not sure about Windows 7 though).

4gb is just barely enough space for an Ubuntu install (lots of people on the forums have 4gb drives in their netbooks), but if you want space left over for data and new apps, you should use the USB Creator instead of the installer. 4gb is also plenty of space for a lighter distro like Puppy.

---

### Post by John Bean on 2009-11-20
> **emigrant said:**
> i went to 'usb startup disk creater' from my current ubuntu, and it says, the tool is to modify essential startup things... :(
You lost me. It's a tool to create bootable USB devices just as its name implies.

---

### Post by jmszr on 2009-11-20
emigrant,

This might be of use to you:[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) and: [http://www.pendrivelinux.com/linux-live-usb-creator/](http://www.pendrivelinux.com/linux-live-usb-creator/)

---

### Post by P4man on 2009-11-20
> **fluffman86 said:**
> You really don't want to do a full install on a USB stick unless you want to wait 10 minutes for it to boot, and another 5 for firefox to start.  It is SOOOO SLLOOOOOWWW..

Hu? Its quite the opposite. A normal install is several times faster than a live environment as you dont need to decompress the image. I boot ubuntu in 30-40s from cheap sandisk cruzer USB stick.  It takes several minutes to do that with a live session

---

### Post by P4man on 2009-11-20
> **emigrant said:**
> My pen is 4gb so i thnk ubuntu is too much. How about puppy linux or an older version of ubuntu may be?

4gb is enough, if only just. If you remove some unneeded packages you get enough working space. I got jaunty on my 4GB stick and 2.6GB is used by ubuntu, the rest is free space, though it has most apps Ill ever need.

---

### Post by fluffman86 on 2009-11-20
> **P4man said:**
> Hu? Its quite the opposite. A normal install is several times faster than a live environment as you dont need to decompress the image. I boot ubuntu in 30-40s from cheap sandisk cruzer USB stick.  It takes several minutes to do that with a live session

That's not my experience, but maybe all of the couple dozen computers I've used it on have REALLY slow USB drives.

---

### Post by Mighty_Joe on 2009-11-20
> **fluffman86 said:**
> That's not my experience, but maybe all of the couple dozen computers I've used it on have REALLY slow USB drives.

I agree with p4man.  I've been using a flash drive with an Ubuntu full install and it boots in seconds.  

[QUOTE=fluffman]
When booting off of a USB drive with a full install, you're pushing something like 4GB into the computer.
[/QUOTE]

Booting a Ubuntu system loads nowhere near 4GB.  The full install takes up more room on the disk than a live CD, but most of that space is taken up by applications, and will only be loaded when the application is run.

---

### Post by P4man on 2009-11-20
> **fluffman86 said:**
> That's not my experience, but maybe all of the couple dozen computers I've used it on have REALLY slow USB drives.

There really is no reason a normal install would be slower. Its exactly the same as installing on to a harddrive except the USB stick has dramatically better access times, and depending on the stick, somewhat worse throughput. I think my stick does ~ 25 MB/s which is roughly comparably to most hdds. Why would it be slower than a hdd then ?

Even if you stick is really slow (some only do ~5MB/s) it should still be faster using a normal install than a live session, because the live session will still need to read and decompress that large image file in to ram. That takes time.

If your boot times are measured in 10s of minutes then something is wrong. Either you are using USB1.1 or the boot process hangs somewhere, but its not normal. By any logic it should be faster than live session and about as fast as a hdd install.

---

### Post by kgas on 2009-11-20
try [slitz linux](http://www.slitaz.org/en/)

---

### Post by emigrant on 2009-11-20
thank you very much for all of your valuable inputs,
as a first step and thinking that the installation time for ubuntu would take more time, i installed puppy through 'live usb creator'. but it seems my mother board won't detect the pen.
does biostar g31 support this?

---

### Post by snowpine on 2009-11-20
> **emigrant said:**
> thank you very much for all of your valuable inputs,
as a first step and thinking that the installation time for ubuntu would take more time, i installed puppy through 'live usb creator'. but it seems my mother board won't detect the pen.
does biostar g31 support this?

You'll likely need to enter the BIOS at boot (usually Esc or one of the Fn keys but it depends on the manufacturer) and choose the USB stick from the boot menu.

I would also recommend using Puppy's own installer. I am not sure that the Ubuntu installer will work with Puppy.

---

### Post by emigrant on 2009-11-20
it wont show usb stick, it only shows, HDD, CD, floppy.

---

### Post by lykwydchykyn on 2009-11-20
> **emigrant said:**
> it wont show usb stick, it only shows, HDD, CD, floppy.

Booting to USB is tricky business on a lot of motherboards -- not always possible even on relatively new devices.  There's a lot of good information at this site: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

If you don't mind a little reading and extra effort, livehelper is in the repositories.  It's a series of scripts that allow you to build up a Debian-based boot CD/USB image from scratch.

Documentation on it is here:

[http://debian-live.alioth.debian.org/](http://debian-live.alioth.debian.org/)

---

