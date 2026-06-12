---
title: "External Hard Drive Mounts Via USB, But Not Via eSATA !"
date: 2010-06-30
forum: General Help
---

### Post by Windows Refugee on 2010-06-30
I have a 1.5TB SATA hard drive, formatted NTFS, in an external enclosure with eSATA & USB ports.  When I connect it to my laptop using a USB cable, it mounts without any problems.  But when I connect it using an eSATA cable, Lucid sees the volume but can't mount it.

I'm using an eSATA cardbus RAID adapter on my laptop that is based on the VIA VT6421 chip. (The laptop has a PATA internal drive.)

I am not trying to implement a RAID configuration, and I'm not even sure that I need to install any drivers to get it to work with eSATA.  I do see it in the left pane in file browser, but it will not mount.  The window that pops up tells me to run chkdsk under Windows.

I downloaded what I believe is the correct driver (via-ide-patch_1.7.0_i386.deb), but when I try to install it, it lists a syntax error while installing, and says "Errors were encountered while processing".

Since I can use the drive via eSATA cable without any problems when booted in Windows, and without any problems via USB cable in Lucid, this looks like a driver or configuration issue relating to the SATA controller.

Any suggestions ?

---

