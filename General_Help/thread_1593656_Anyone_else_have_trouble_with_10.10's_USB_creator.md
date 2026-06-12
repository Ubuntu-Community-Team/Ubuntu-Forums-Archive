---
title: "Anyone else have trouble with 10.10's USB creator?"
date: 2010-10-11
forum: General Help
---

### Post by Astnya on 2010-10-11
I installed Maverick yesterday on both my laptop (32-bit) and desktop (64-bit). So far I'm liking it except for a couple of minor issues, and this is one that I feel is worth pointing out.

Last night I was troubleshooting a wireless problem on the laptop and I tried to boot from a USB drive onto which I had added an image for 10.04 using 10.10's usb-creator-gtk (the Startup Disk Creator in the Administration menu). After the BIOS screen I got this error:

```
SYSLINUX 4.01 debian-20100714 EDD Copyright (C) 1994-2010 H. Peter Anvin et al
Unknown keyword in configuration file: gfxboot
vesamenu.c32: not a COM32R image
boot:
vesamenu.c32: not a COM32R image
boot:
(...)
```Huh. I redid the disk... same error. I swapped flash drives... same error. I knew that it was highly unlikely that both my flash drives had developed the same glitch simultaneously, so I went over to another computer, running 10.04, and redid the drive on there. Surprise, surprise: it worked. I was able to boot from the flash drive.

Up until then I'd been using the usb-creator-gtk on my 64-bit desktop. I haven't tested the 32-bit version on my laptop, but I suppose the problem could be with the 64-bit version only. Anyway, I don't really know what the error means and I don't know what could have caused it. I wonder if anyone else has had, or has heard of, similar issues?

---

### Post by sendblink23 on 2010-10-11
wiped

---

### Post by adoomer on 2010-10-11
This issue has been described in Maverick release notes:
"It is not possible to create Ubuntu 10.04 USB disks from the  Startup Disk Creator in Ubuntu 10.10 due to a backwards incompatibility  in the syslinux program."

Source: [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common Desktop Applications]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common%20Desktop%20Applications")

---

### Post by Astnya on 2010-10-11
> **adoomer said:**
> This issue has been described in Maverick release notes:
"It is not possible to create Ubuntu 10.04 USB disks from the  Startup Disk Creator in Ubuntu 10.10 due to a backwards incompatibility  in the syslinux program."

Source: [https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common Desktop Applications]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Common%20Desktop%20Applications")
Thank you. I didn't know that page existed. I can only assume that there will be a fix at some point, hopefully soon; in the meantime., I'll keep Lucid around on a computer for making USB disks.

---

### Post by ikt on 2010-10-12
great timing on the post, I have just run into this issue...

---

### Post by wata on 2010-10-13
I ran into the same problem when trying create a USB boot to downgrade from 10.10 back to 10.04, because evolution-exchange doesn't work under 10.10 (but that's another story).

There's a super easy workaround for this USB creator issue for those wanting to go back to 10.04:
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/)

---

### Post by MorayJ on 2010-10-22
Not sure if it's the same thing, but I got the same COM error and just hitting tab worked so I was shown the various boots (live, install, etc).

I typed live and away we went. Didn't try the others. 

Just doing an install from live and it seems to be working.

Cheers
Moray

---

### Post by masterdje on 2010-10-24
Same here ... bad afternoon...
from 10.10  desktop 32b
> making 10.04 usb reinstall stick : no problem
> 9.10 : vesamenu.c32  : not a com32R
> 9.04 : vesamenu.c32  : not a com32R

thank you, Morayj, "tab" was the point !!

---

### Post by GoWest5 on 2010-11-14
Thank you Moray.  Your solution also worked for me using Mint 10  Creator for making a USB Stick. 
I had tried typing "help" and then ENTER but that did not work.


> **MorayJ said:**
> Not sure if it's the same thing, but I got the same COM error and just hitting tab worked so I was shown the various boots (live, install, etc).

I typed live and away we went. Didn't try the others. 

Just doing an install from live and it seems to be working.

Cheers
Moray

---

### Post by Morpholinux on 2010-11-17
I try to install Xubuntu 10.04 in an old Desktop..
(compaq presario SR1405LA) without O.S. 

I got the same error
then <TAB>
..live
the installation process freezes when it gets to 85%
then after a few hours I turn it off
..live-install
second time the installation process told me that already have an O.S. but Ubuntu 10.04 (..so I get a little confused)...it freezes to 75%

I did try the check, the memtest and the mainmenu options (which only the last one doesnt work)
..could not install the system....

---

### Post by pepsifx357 on 2010-11-28
Is there a work around like using UNetbootin?  I'm kinda in a spot and need a USB stick with 10.04 on it.

---

### Post by oldfred on 2010-11-28
Just install grub2 to the flash drive and copy the iso to the drive. Edit grub.cfg to loopmount the ISO.

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
boot from hard drive
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by pepsifx357 on 2010-11-28
> **oldfred said:**
> Just install grub2 to the flash drive and copy the iso to the drive. Edit grub.cfg to loopmount the ISO.

 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
boot from hard drive
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)


I've always wondered how this worked, THANKS!

Is it possible to have multiple livecd ISOs on a single external hard drive and flip through them through grub using this method?

---

### Post by oldfred on 2010-11-28
I have several Ubuntu's, Parted Magic, System Rescue, gparted, and puppy (but it is not loopmounted) all on my 4GB flash drive.

I prefer this for installs as I just copy my Ubuntu ISO and edit grub config with the new name and I am good to go.

I only tested booting from the hard drive but that works. 

Two scripts that automate the install.

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
multicd.sh - combine Linux ISOS into one
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)

---

### Post by C.S.Cameron on 2010-11-29
You can make a grub2 iso install of Ubuntu, or other Debian derivative, persistent by editing the grub.cfg menu entry similar to the folowing:
"linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso noeject noprompt -- **persistent**"
and create a ext2, 3 or 4 partition named casper-rw.
If you wish a seperate home partition name it home-rw.

Note that persistent has a space before it.

---

### Post by sabitha on 2011-02-06
> **Astnya said:**
> I installed Maverick yesterday on both my laptop (32-bit) and desktop (64-bit). So far I'm liking it except for a couple of minor issues, and this is one that I feel is worth pointing out.

Last night I was troubleshooting a wireless problem on the laptop and I tried to boot from a USB drive onto which I had added an image for 10.04 using 10.10's usb-creator-gtk (the Startup Disk Creator in the Administration menu). After the BIOS screen I got this error:

```
SYSLINUX 4.01 debian-20100714 EDD Copyright (C) 1994-2010 H. Peter Anvin et al
Unknown keyword in configuration file: gfxboot
vesamenu.c32: not a COM32R image
boot:
vesamenu.c32: not a COM32R image
boot:
(...)
```Huh. I redid the disk... same error. I swapped flash drives... same error. I knew that it was highly unlikely that both my flash drives had developed the same glitch simultaneously, so I went over to another computer, running 10.04, and redid the drive on there. Surprise, surprise: it worked. I was able to boot from the flash drive.

Up until then I'd been using the usb-creator-gtk on my 64-bit desktop. I haven't tested the 32-bit version on my laptop, but I suppose the problem could be with the 64-bit version only. Anyway, I don't really know what the error means and I don't know what could have caused it. I wonder if anyone else has had, or has heard of, similar issues?
](*,)
to correct this problem you must use the appropriate *.c32 from the correct version of syslinux

but you ca just copy your syslinux version stuff to usb and reinstall syslinux
assuminng usb is sdb1 and mounted at /media/disk
open terminal, become root with "sudo su" plus your password and


> 
cp -r /usr/lib/syslinux/vesamenu.c32 /media/disk/syslinux/

syslinux /dev/sdb1

on slackware syslinux is in /usr/share

this work and tested with me...\\:D/
Info :
```
http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/#post4205365
```

---

### Post by texla on 2011-02-22
sabitha: 

to correct this problem you must use the appropriate *.c32 from the correct version of syslinux

but you ca just copy your syslinux version stuff to usb and reinstall syslinux
assuminng usb is sdb1 and mounted at /media/disk
open terminal, become root with "sudo su" plus your password and


Quote:
cp -r /usr/lib/syslinux/vesamenu.c32 /media/disk/syslinux/syslinux /dev/sdb1

on slackware syslinux is in /usr/share

Thx, Sabitha - This worked for me, too - what a weird bug to have no way to use the last release in the usb startup creator.  Thanks for the fix - not sure why it worked because I couldn't get the line of the terminal to go through without an eror but it did apparently with just the copying of the syslinux folder so I'm ok with it.

---

### Post by deconstrained on 2011-02-22
[http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/#post4120867](http://www.linuxquestions.org/questions/linux-mint-84/trying-to-boot-linux-mint-9-from-usb-flash-drive-vesamenu-c32-not-a-com32r-image-829397/#post4120867)

Ask Google and ye shall receive.

---

### Post by Isidorito on 2011-05-22
The Option of "Tab Button" Worked for me at installation of BackTrack 5

---

### Post by neorg on 2012-02-08
Just type **install** after boot:

---

### Post by tigerstyle on 2012-07-14
> **MorayJ said:**
> Not sure if it's the same thing, but I got the same COM error and just hitting tab worked so I was shown the various boots (live, install, etc).

I typed live and away we went. Didn't try the others. 

Just doing an install from live and it seems to be working.

Cheers
Moray

This did it for me! Cheers Moray!

---

