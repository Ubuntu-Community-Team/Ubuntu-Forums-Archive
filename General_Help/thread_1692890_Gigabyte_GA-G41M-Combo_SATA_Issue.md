---
title: "Gigabyte GA-G41M-Combo SATA Issue"
date: 2011-02-22
forum: General Help
---

### Post by WiseHacker on 2011-02-22
Hello there.  This is bound to be a long story but I will keep it as brief as possible.

I recently built a small PC to act as a media server.  It originally consisted of an IDE 80 GB hard drive, 2 GB of RAM, GeForce 8500 GT, a Pioneer SATA DVD/RW drive and a Gigabyte G41M-Combo motherboard.

After construction I installed Ubuntu 10.10 and started to use it for streaming and video encoding.  Naturally the space started to run out.

So, I installed a 1 TB SATA II (Seagate Barracuda) hard drive.  The drive installed fine but I noticed that reading and writing to it was a bit slow.  Thus I used hdparm and found that the drive was not being treated as a SATA drive.  This fact was confirmed when I looked at the Disk Utility (it says that the drive is connected to an Intel N10/ICH7 PATA Controller) and an examination of dmesg shows that the mother board has a SATA IDE controller.

Naturally, to solve this, I first checked to see if my BIOS was up to date - I found I was running the latest version.  Next I went into the settings and found that SATA was initially set to "Combine" thus causing all devices to be treated as PATA devices.

Obviously, I change the setting to "Enhanced" - in theory forcing all SATA devices to be treated as SATA devices and all IDE as PATA.  However, after booting into Ubuntu again, it is still seeing my hard drive (and optical drive) as being attached to a PATA controller.

Am I missing something here?  I come from a Windows environment thus I am not well versed in changing kernel modules - I am used to simply updating drives on Windows (XP through to 7).

My thanks in advance for anyone that can clarify this for me.  I am starting to think that SATA on this motherboard is not supported in Ubuntu.

---

