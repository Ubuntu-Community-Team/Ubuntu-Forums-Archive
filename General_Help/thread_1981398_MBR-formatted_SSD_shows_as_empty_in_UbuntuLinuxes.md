---
title: "MBR-formatted SSD shows as empty in Ubuntu/Linuxes"
date: 2012-05-16
forum: General Help
---

### Post by Objekt on 2012-05-16
I recently built a new system with an Intel Series 520 SSD as the main drive.  I'm having some really strange problems with Ubuntu and all other Linux-based tools and distros I've tried so far.

Briefly, the SSD, although formatted as MBR, is not recognized either in a live Ubuntu 10.04 session, or a live Linux Mint 12 session, or by Gparted or Clonezilla.

Accordingly, I am unable to set up a dual-boot of any flavor of Linux so far, nor can I use Clonezilla, my favorite disk imaging tool.

In all these cases, the SSD shows as "unallocated," as if it didn't contain any partitions at all.  Yet, it does contain an active installation of Windows 7 Ultimate, with the usual division of a small (ca. 130 MB) reserved/boot partition and the rest an NTFS volume containing Windows itself.

Could this be related to the fact that I originally had the SSD set up as a GPT volume?  I subsequently reformatted the SSD as an MBR disk whilst reinstalling Windows 7 (long story!).  I would have thought the re-format would have made the SSD act like any ordinary, MBR-provisioned hard drive.

Is it some kind of hardware incompatibility?  The motherboard is a Gigabyte GA-Z77-DS3H.  It has UEFI but I didn't think that meant it would be incompatible with Linux and Linux-based bootable utilities.

ps: Like the new Ubuntu forums look.  Very snazzy!

---

### Post by ajgreeny on 2012-05-16
To properly remove any GPT formatting I think you need to write a new partition table, easiest with gparted using the Device > New partition table menu entry.

---

### Post by oldfred on 2012-05-16
gpt has a backup partition table near/at the end of the drive. Windows only overwrites the primary partition table as it does not look at the backup. Linux tools see the backup and get confused on whether it is MBR or gpt.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

There have been several posts on the new z77 boards. Some do work as there have been Linux performance tests. But one user gave up and installed Ubuntu on another computer, several reverted to BIOS/MBR mode, and I think a couple did make it work, but only by partitioning in gpt in advance. Several issues and bugs still with the newest Ubuntu, any older versions would not work as hardware is too new.

---

### Post by Objekt on 2012-05-16
Hmm.  I guess the backup GPT would explain why Windows "thinks" the disk is MBR, but Linuxes get confused.

The Windows 7 installer doesn't allow you to specifically select one sort of partitioning scheme or the other - it's obfuscated, whether intentionally or not.  I got GPT on the first install entirely by accident.

I hope this doesn't mean I have to end up installing Windows 7 yet a third time.  That's a real pain.

So, I'll use Windows 7's built-in system imaging tool to save a backup before I try FixParts et al.

---

### Post by oldfred on 2012-05-16
With both Windows & Ubuntu and a UEFI system, how you boot install CD/DVD/Flash determines whether system will install in UEFI or BIOS mode. Both systems when you choose to boot from UEFI should offer two modes one UEFI and the other BIOS/AHCI/legacy or some other name which seems to vary by vendor.

---

### Post by Objekt on 2012-05-17
Fixparts did the trick.  There was indeed some orphaned GPT stuff that was causing the disk to show up as unallocated.  So I ran Fixparts, and now all is fine.  Thanks!

---

