---
title: "a problem with my disk space"
date: 2011-02-27
forum: General Help
---

### Post by docoon on 2011-02-27
Is my first day using ubuntu linux and i will first ask b4 doing a possible ****
I was going to add in to my linux driver more 20 gigabytes(by windows) but when i saw it till have about more than 8 gb of free space... but when I'm on ubuntu it says that i only have 2 gb, but that make no sense... I don't know if that is complete normal and weird or is complete bug ... for who didn't understand yet : at windows 7, the total disk is 17,5 GB and 8,58 GB is full and 8,99 is empty but when i go to ubuntu it says my drive only have more 2GB empty...
as screen>>
_ps: i install my ubuntu in to drive L (''Linux Luke'')_
[IMG]http://i55.tinypic.com/wi7bt2.png[/IMG]

[IMG]http://i53.tinypic.com/5e7abl.png[/IMG]

At Linux.
[IMG]http://i53.tinypic.com/303begy.png[/IMG]



So what should i do? to fix the problem disk space...

---

### Post by grahammechanical on 2011-02-27
I would say, do not fix what is not broken. Or to put in in my local dialect: don't fix wot ain't broke.

You are not comparing like with like. You should use Disk Utility to compare what is says about the 500 GB Hard Disk ATA SAMSUNG HD502-HI with what windows 7 is saying about your hard disc.

You say:

> ps: i install my ubuntu in to drive L (''Linux Luke'')And yet you point Disk Utility to Linux Loop:root.disk. I do not know what that is, but I do not think that it is part of your hard disc. Could it be a USB flash drive?

Where ever you installed Ubuntu there should be a partition called Swap. Disk Utility will show it. It does not show it on Linux Loop:root.disk.

I have just looked at this link

[http://en.wikipedia.org/wiki/Loop_device](http://en.wikipedia.org/wiki/Loop_device)

I do not understand everything that I read there but I am guessing that you are looking at a Ubuntu Live installation on a USB flash drive.

Regards.

---

### Post by poodoopealeoaph on 2011-02-27
Well your problem is that once you install ubuntu, your partitions are set. So, it is pretty difficult to steal some space from winblows and put it to your ubuntu partition. Even though it sounds like a hastle, you may have better luck if you just reinstall ubuntu and during the install go to your advanced settings and set your partitions as the sizes you really want.

---

### Post by docoon on 2011-02-27
> **poodoopealeoaph said:**
> Well your problem is that once you install ubuntu, your partitions are set. So, it is pretty difficult to steal some space from winblows and put it to your ubuntu partition. Even though it sounds like a hastle, you may have better luck if you just reinstall ubuntu and during the install go to your advanced settings and set your partitions as the sizes you really want.


ok, i will try to reinstall ubuntu...
thanks m8...

ahh by the way thanks grahammechanical too :D

---

### Post by Mark Phelps on 2011-02-28
The root.disk clearly indicates that you installed via Wubi -- the reference to "L" should have told folks that as well.

It's not a simple matter to expand a Wubi installation to allocate more space after the install is done.

Also, you can NOT use traditional partitioning utilities as Wubi does not use a standard partitioning scheme.

Also, you didn't mention your Window OS (or, I missed it), but if you're using Vista or Win7, do NOT use GParted or the Ubuntu installer to resize your Windows OS partition.  Doing so runs the risk of corrupting that and rendering it unbootable.  Instead, use the Vista/Win7 Disk Management utility to shrink an NTFS partition to make room for Ubuntu.

Also you can not have more than 4 primary partitions on a drive.  If you use GParted or the Ubuntu installer to force a creation over that limit, you risk turning your entire PC into Dynamic Disks -- courtesy of MS.

---

### Post by bcbc on 2011-02-28
Yes Mark Phelps is right - it's a wubi. Wubi installs to a virtual disk that is fixed in size. So when it reports free space it's looking on the virtual disk only, not on the /host partition.

Reinstalling and selecting a bigger install size will fix that (**note** reinstalling will delete everything on Ubuntu).

Wubi is OK to try out Ubuntu. Eventually if you use it a lot you'll want to do a proper install. In the meantime, you can prevent problems by locking grub-* packages (see the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198")) and also keep important data backed up outside of the wubi virtual disk.

---

