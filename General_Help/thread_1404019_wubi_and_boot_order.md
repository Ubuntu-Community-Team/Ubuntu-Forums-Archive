---
title: "wubi and boot order?"
date: 2010-02-10
forum: General Help
---

### Post by bfcrowrench on 2010-02-10
Hi.   This is a hail mary pass I'm doing.  Hopefully someone help or at least point me toward help.

To summarize my problem (which I will then explain in full), I'm hoping someone with some intimate knowledge of wubi can tell me whether or not it is possible for a wubi installer to do "weird" things to my device boot order.

My goal is to get my computer to boot from a SATA device.  The tricky part is that my SATA controller is on a PCI card.

The first time I hooked up a SATA drive, I found that my computer would not boot my system drive (which is currently the master disk on my motherboard's primary IDE controller).   If I booted the machine with the SATA drive disconnected, my system booted;  so my indefinite workaround solution was to hotplug the SATA disk after the system started booting.

Lately I wanted to install a new system to the SATA drive, but I discovered that the system no longer wants to boot a SATA drive.  In fact, I discovered that it is no longer necessary to hotplug the SATA drive after booting;  I can just leave the SATA drive attached all the time and it doesn't bother the system disk like it used to.

I really can't say when this change came about; I'm exploring the possibility that this change might have resulted from a wubi installer which made some changes to my system (which is presently Windows XP).

Somehow my system went from booting SATA first to booting Primary IDE first.   If wubi did this somehow, it would help me immensely to know that -- and to know what I can do to reverse that.

Thanks everyone!

~b

---

### Post by NightwishFan on 2010-02-10
I believe Wubi actually uses the Windows bootloader. Generally boot order is a bios option.

---

### Post by bfcrowrench on 2010-02-11
> **NightwishFan said:**
> I believe Wubi actually uses the Windows bootloader. Generally boot order is a bios option.

Thanks for the reply.   That was my belief too, so I started there but haven't had any success.   I guess you'd say I'm getting desperate :-(

---

### Post by Mark Phelps on 2010-02-11
> **bfcrowrench said:**
> Thanks for the reply.   That was my belief too, so I started there but haven't had any success.   I guess you'd say I'm getting desperate :-(

Once you have Wubi installed, and get a boot selection menu, you can change the order following the instructions in the Wubi Guide:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?")

---

### Post by bfcrowrench on 2010-02-14
> **Mark Phelps said:**
> Once you have Wubi installed, and get a boot selection menu, you can change the order following the instructions in the Wubi Guide:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20make%20Ubuntu%20the%20default%20boot%20option?")

I think you're talking about making NTLDR choose whether to boot Windows or the Wubi installation of Linux by default?

I'm trying to do something else:  I'm just trying to get my PC to boot a standard installation of Linux (non-Wubi) from a separate physical hard drive.   Strange as it sounds, it would seem that the Wubi installation is affecting more than the hard drive it was installed to.

I will elaborate on this in my next post.

---

### Post by bfcrowrench on 2010-02-14
I'm back with evidence of weird things going on to my PC related to Wubi.

To make any sense of what I'm going to describe, I need to first explain my hardware setup.

My motherboard has 2 integrated IDE controllers, and I have PCI card for added SATA support.   The SATA card supports 1 internal SATA connection and one external (eSATA) connection.  I'm utilizing all the connectors, both IDE and SATA.

Primary Master (0,0) boots Windows XP.  This is my current system drive.
Primary Slave (0,1) boots Windows XP, a separate system from years ago.
Secondary Master (1,0) boots NetBSD.
Secondary Slave (1,1) is my CD drive.

I don't know how the SATA drives are addressed or handled internally yet, but one of them is formatted as NTFS and *to my knowledge* has nothing in its MBR.   The other one is dedicated to my new Linux installation (ext4 & swap, i'd expect); its MBR boots Grub.

The new Linux drive is in an external enclosure which gives me the option to switch between eSATA and USB.  It will boot Grub when booted by USB, not when booted by SATA.   It makes no difference whether it is connected by SATA or eSATA, the behavior is the same.

The Primary Master copy of Windows XP is where I installed Wubi months ago.  Specifically I mean, this is the system under which I ran the Wubi installer, and theoretically the disk that should be affected.   The actual data for the Linux system was stored on the NTFS-formatted SATA drive.

Hopefully all that makes sense (please don't make my try to justify all that nonsense, just accept for now that I did it).


So what I did today was to try again to boot Linux from the SATA drive by selecting the SCSI option in my BIOS's boot order.  This failed, so I was going to set it back when I decided to try some other options just to see what they did.  There is a specific CDROM option, and then there are HD0 through HD3 (that's four HDs).   Since that's more HDs than I have connected in IDE, I thought I might try them all just to see if one of them automagically referenced my SATA drive.

Unfortunately, it did not.   However, what did eventually happen was unexpected.

As I was booting each disk, I got to the old, previous installation of Windows XP on (0,1).   And get this folks:  before it booted into XP, **it gave me the menu asking me to choose between my wubi installation of Linux and Windows.**

I can't understand why that would happen.   As i understood it, Wubi should be confined to the MBR of the hard drive of the Windows system where it was installed.   This is a separate disk.  How is Wubi affecting its bootloader?

I plan to do more experimentation by actually disconnecting certain disks to see how booting is affected.   I will update with information as I gather it.

---

### Post by bfcrowrench on 2010-02-14
I just booted (0,1) with (0,0) disconnected.  Now I get a brief message in caps about NTLDR being missing, press any key.   Just earlier when (0,0) was connected it booted, albeit after the choice between Windows and the wubi Linux.   In the past, the bootloader worked fine independently of (0,0).  So that's an unpleasant development..

---

### Post by bfcrowrench on 2010-02-14
More developments:  While Wubi may have made a mess of my MBRs, it may not be the key to getting this SATA drive to boot.  I'm not really sure.

I explained early on in this thread that my SATA drives used to halt up the boot sequence when they were connected at boot-time;  my work around was to hotplug them after booting up.   Then at some point after installing Wubi, this was no longer an issue.   And that's why i started suspecting Wubi was involved in my problem.

Well, I'm now able to reproduce the situation where I have to hotplug the SATA drives after booting.

Earlier when I had the problem, my boot sequence was Floppy, CDROM, HD0.   It had been that way for a long time.   For whatever reason, the SATA drives were interfering with the boot order in spite of not actually appearing in the boot order.

Then quite recently I changed it to CDROM, USB-HDD, HD0;  this allowed me to boot the SATA drive using the external enclosure.

Now the boot order is CDROM, SCSI, HD0.  When a SATA disk is connected, it hangs trying to boot.  When the SATA disks are disconnected, it boots the master disk of my primary IDE controller just fine.

It is curious to me that this boot order change occurred at all, annoying that the MBR of my primary slave is fubared, and more than suspicious that all of these things happened following a Wubi installation.

For the time being however, it seems I'm back to where I was before;  so until Wubi raises its head again and appears to be interfering some more, I'm gonna forget about it for now and focus my attention to booting my SATA disk.

Thanks for your attention to this issue.

---

