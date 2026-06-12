---
title: "Backup Strategy - will or won't this work?"
date: 2009-07-08
forum: General Help
---

### Post by stevecoh1 on 2009-07-08
I have a Dell Inspiron 530.  It came with a 320 GB HD.  I later purchased an identical 320 GB HD.  I use this occasionally to back up the system when I'm about to perform a dangerous activity such as an OS upgrade.  It has saved my life on several occasions.  Grub does not know about the second drive.  I use Clonezilla live CD to make the backup clone.  

Since the upgrades weren't working for me (not even 8.04 -> 8.10) I adopted a different strategy and made a fresh install of 9.04 on one of the drives, then booted it and mounted the old 8.04 drive and pulled a bunch of stuff over which was mostly in my home directory.  This went remarkably smoothly.

But I would also like to use the second drive as follows.

Every night have cron issue a DD command to copy the main drive byte for byte to the new one, to keep my system dynamically backed up.  Should I experience hard drive trouble, I could just boot off the other drive.  But will I run into problems with two bootable drives?  The BIOS lets me choose which hard drive to boot off but I am not sure that this is completely reliable.  What are the issues with having two identical drives connected to the PC in this way?

---

### Post by ktmom on 2009-07-08
I thought the Inspiron 530 has a RAID option in the BIOS.  What your describing sounds like a manual RAID 1 setup.  You don't want to use RAID because a change on one drive is mirrored on the second drive?

---

### Post by stevecoh1 on 2009-07-08
Good question!

The reason is mostly simple ignorance.  I've never set up a RAID before.  Previous attempts in that direction indicated that I might have to change my system (which is actually a dual boot with Windows, by the way).  But if you're telling me it's as simple as a BIOS setting switch I might have a look.

One more thing - is it as easy to UNHOOK this RAID- as when I might want to upgrade this system again?  Then I could turn it off and go with the upgrade and only turn it back on when the upgrade was finished.

---

### Post by az on 2009-07-08
The problem with booting off a setup with two identical drives is that the filesystem(s) on each drive will have the same ID.  If you mount your filsystems by ID (which is the default), then you are not completely sure that you are actually using the correct drive.

Using a mirrored raid will work, since you will be able to mount only one drive and use it, but I don't think you will be able to do that straightforwardly by simply disconnecting one drive.  Raid may be overkill too.  

What is important to you?  Perhaps simply backing up the things that are not replaceable is a better and more efficient strategy.  It will decrease your disk use, too.  Think of it, if you are going to read and write the entire drive, bit-for-bit every day, that's a lot of time, power and wear-and-tear for nothing.

So, can you just back up the files in your home folder?

---

### Post by stevecoh1 on 2009-07-09
> **az said:**
> The problem with booting off a setup with two identical drives is that the filesystem(s) on each drive will have the same ID.  If you mount your filsystems by ID (which is the default), then you are not completely sure that you are actually using the correct drive.

Using a mirrored raid will work, since you will be able to mount only one drive and use it, but I don't think you will be able to do that straightforwardly by simply disconnecting one drive.  Raid may be overkill too.  

What is important to you?  Perhaps simply backing up the things that are not replaceable is a better and more efficient strategy.  It will decrease your disk use, too.  Think of it, if you are going to read and write the entire drive, bit-for-bit every day, that's a lot of time, power and wear-and-tear for nothing.

So, can you just back up the files in your home folder?

You raise many good points.  My idea was to have 0 downtime in event of a hard-drive failure but do I really need that?  In the old days, say 2 or 3 years ago, with a RedHat install and junk littered all over the drive, it was pretty painful.  But Ubuntu's apt-get system is pretty darned easy to use (redhat now has something similar of course) and I'm a bit more disciplined now about where I put stuff.  Based on my experience this week of being forced to do a new install instead of the upgrade I wanted to do, which turned out to be much less unpleasant than I was expecting it to be, I would have to say "no, I don't need **zero **downtime".  It's just a fairly heavily-used home PC that I do some of my work on.  No really mission-critical stuff lives outside my home directory and even there one could question its mission-criticality.

Backing up the home directory only might be the sweet spot.  I don't mind being down for a few hours, which is all it took me to get back up and running.  Thanks for helping me get my head straightened out.

---

