---
title: "Can't detect CD / DVD drive!!  Can't run Live CD !!!"
date: 2005-03-08
forum: General Help
---

### Post by ubuntu_seeker on 2005-03-08
> As with Array CDs 4 and 5, this release includes both the Install CD and
the Live CD.

This is scheduled to be the last Array CD release before the Hoary
Preview. As such, we'd very much appreciate anyone who can test it to do
so and file bugs on any problems you encounter.


Ok, bug / problem fix sought ;) :):

I'm booting Ubuntu Hoary Live CD (Array 6 and the MD5SUM checked out fine) and it boots ok and begins detecting various pieces of hardware but coughs on the CD/DVD drive, meaning, it could not find a driver for my CD/DVD so then I have to stop the installation.  That is, I keep ending up back at the install menu where it says that the CD drive has not been detected yet.  It asks me if I want to pick a driver from a list, and I've tried various ones "cdrom" etc. with no luck.

I've seen others post about this same problem in several places (at least 3 threads), but still there have been no replies... hoping for one soon.  :)

My hardware is: Dell XPS Gen 3 (Pentium 4 3.6 GHZ), DDR-2 RAM, SATA 7200 rpm hard drive.

The CD-ROM is a CD / DVD RW combo drive...  I believe it's an IDE drive.. listed in XP properties as "HL-DT-ST DVD+RW GRA-4120B".

MEPIS had no problem detecting my CD drive. And the drive works just fine in Windows XP SP2.

Thanks for any ideas!!! :^D.

I'd really like to be able to try out the live CD before installing Ubuntu. I'd much prefer to go with Hoary since Warty is kinda out of date by now.

I wish I could install Ubuntu    ](*,)

---

### Post by alastair on 2005-03-08
It's a hard one to know for sure. Try n=booting the CD with either (or both?) :

linux acpi=off

linux ide=nodma

Worth a try ...

---

### Post by ubuntu_seeker on 2005-03-08
I tried linux ide=nodma, but will try acpi...

Thanks for the suggestion!!!  :)

All help greatly appreciated.   :grin:

---

### Post by dcstar on 2005-03-09
[QUOTE=ubuntu_seeker]Ok, bug / problem fix sought ;) :):

I'm booting Ubuntu Hoary Live CD (Array 6 and the MD5SUM checked out fine) and it boots ok and begins detecting various pieces of hardware but coughs on the CD/DVD drive, meaning, it could not find a driver for my CD/DVD so then I have to stop the installation.  That is, I keep ending up back at the install menu where it says that the CD drive has not been detected yet.  It asks me if I want to pick a driver from a list, and I've tried various ones "cdrom" etc. with no luck.

I've seen others post about this same problem in several places (at least 3 threads), but still there have been no replies... hoping for one soon.  :)

My hardware is: Dell XPS Gen 3 (Pentium 4 3.6 GHZ), DDR-2 RAM, SATA 7200 rpm hard drive.

The CD-ROM is a CD / DVD RW combo drive...  I believe it's an IDE drive.. listed in XP properties as "HL-DT-ST DVD+RW GRA-4120B".
......[/QUOTE]
Is the drive set as a "Slave" on a port with no "Master" device?

If so, try changing it to "Master" and see if that makes a difference.

---

### Post by ubuntu_seeker on 2005-03-09
[QUOTE=dcstar]Is the drive set as a "Slave" on a port with no "Master" device?

If so, try changing it to "Master" and see if that makes a difference.[/QUOTE]

Hmmm...  umm this is my main system hard drive, and I only have 1 drive.  So I assume it must have been set to "Master" by the manufacturer, Dell, right?  There are no other hard drives attached.

But I did see one guy said that Hoary Array 6 does not yet support SATA hard drives, and mine is SATA.  Seems weird that a hard drive would stop the CD drive from being detected... especially when the CD is being *used* by the Live CD to even get to the point where it could detect the drive it is already running in...

Oh well, at least Fedora Core 3 works like a charm at work...  ehe.

I'd like to try Ubuntu when SATA is finally supported.  :)

---

### Post by dermotti on 2005-03-10
i use sata on hoary no probem

---

### Post by dcstar on 2005-03-10
[QUOTE=ubuntu_seeker]Hmmm...  umm this is my main system hard drive, and I only have 1 drive.  So I assume it must have been set to "Master" by the manufacturer, Dell, right?  There are no other hard drives attached.

But I did see one guy said that Hoary Array 6 does not yet support SATA hard drives, and mine is SATA.  Seems weird that a hard drive would stop the CD drive from being detected... especially when the CD is being *used* by the Live CD to even get to the point where it could detect the drive it is already running in...

Oh well, at least Fedora Core 3 works like a charm at work...  ehe.

I'd like to try Ubuntu when SATA is finally supported.  :)[/QUOTE]
I was referring to the CD/DVD, which I assume was a "standard" IDE drive.

Sometime your BIOS will boot off a Slave or Master drive, but the O/S later has problems if there isn't a Master.

In the past I've seen a lot of CD drives left set to "Slave" on the assumption that they will be plugged into the same cable as a "Master" hard drive.

If the hard drive is actually a non-IDE drive (like SCSI or SATA) then they don't bother to reconfigure the CD to "Master", basically because Windows doesn't care - even if some other things do!

---

### Post by ubuntu_seeker on 2005-03-11
How do you set the CD / DVD drive to be Master??  :)

thanks

---

### Post by ubuntu_seeker on 2005-03-11
Ok, I checked in my BIOS and it says I have the drive on Parallel ATA (PATA) and that it is set to PRI(mary?) IDE Master... I suppose that means that the physical jumper must be set to Master on that drive..  I guess I may crack open the case later and check to see if I can tell.

So maybe the Master / Slave thing is not the problem...

Another guy with this problem said he solved it this way:

"I have this issue (also with a Dell), if you do a dmesg on the terminal and if you get something simular to this...

ide0: I/O resource 0x1F0-0x1F7 not free.
ide0: ports already in use, skipping probe
ide1: I/O resource 0x170-0x177 not free.
ide1: ports already in use, skipping probe

then thats looks to be the reason, I believe it's because the SATA driver is loaded before the ide-generic drivers.. Didn't get around it, but I installed Ubuntu by booting up from a gentoo CD, partitioned/formatted the drives and then copied the Ubuntu CD/DVD to one of the partitions.

On booting from the Ubuntu CD I mounted the said partition to /cdrom and then continued with the install.

Once installed I still got the same issue but followed this link to solve...

http://kerneltrap.org/node/3971"

---

### Post by dcstar on 2005-03-12
[QUOTE=ubuntu_seeker]Ok, I checked in my BIOS and it says I have the drive on Parallel ATA (PATA) and that it is set to PRI(mary?) IDE Master... I suppose that means that the physical jumper must be set to Master on that drive..  I guess I may crack open the case later and check to see if I can tell.

So maybe the Master / Slave thing is not the problem...
......."[/QUOTE]

Yep, can't help you with it any more if it already is a Master - good luck!

---

### Post by ubuntu_seeker on 2005-03-12
> Yep, can't help you with it any more if it already is a Master - good luck!
__________________
Regards, David.
Thanks, yeah, I actually did run dmesg and got exactly what the other guy did:

> 

I have this issue (also with a Dell), if you do a dmesg on the terminal and if you get something simular to this...

ide0: I/O resource 0x1F0-0x1F7 not free.
ide0: ports already in use, skipping probe
ide1: I/O resource 0x170-0x177 not free.
ide1: ports already in use, skipping probe

then thats looks to be the reason, I believe it's because the SATA driver is loaded before the ide-generic drivers.. Didn't get around it, but I installed Ubuntu by booting up from a gentoo CD, partitioned/formatted the drives and then copied the Ubuntu CD/DVD to one of the partitions.
That won't help me to run the live CD, so I'm about to try Hoary Preview release live CD and see if that helps... if not then I guess I can try waiting till April... ;)  :)

Thanks to all for their help.  :)

---

### Post by ubuntu_seeker on 2005-03-12
Oh well.. no joy.. Hoary Preview has the exact same problem and still cannot detect my CD / DVD drive.

Apparently the only fix possible for a live CD is this:

"Wait for fix in ata_piix"

taken from the following solution if you want to do an HD install:

[http://kerneltrap.org/node/3971](http://kerneltrap.org/node/3971) --
> 
Solved
Comment posted by Anonymous on Friday, October 15, 2004 - 11:07

Bug with ata_piix module prevent loading ide driver. You have to rebuild initrd image. Just add following to /etc/mkinitrd/modules:
ide-generic
ata_piix
sd_mod

Backup your old initrd:
cp /boot/initrd.img.2.6.8-1-686 /boot/initrd.img.2.6.8-1-686.bak

Make new initrd image:
mkinitrd -o /boot/initrd.img.2.6.8-1-686

Reboot
In case of failure boot from old image - grub way:
initrd /boot/initrd.img.2.6.8-1-686.bak

Wait for fix in ata_piix

Best regards

Pavel Tavoda
I hope there is a fix for ata_piix soon because right now that bug means that a TON of Dell machines and probably others cannot run Ubuntu Live CD.

---

