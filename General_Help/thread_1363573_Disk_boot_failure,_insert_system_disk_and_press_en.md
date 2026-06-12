---
title: "Disk boot failure, insert system disk and press enter"
date: 2009-12-24
forum: General Help
---

### Post by lasleym on 2009-12-24
Running 9.10 with 1MB of RAM and an Intel Pentium 4 CPU 2.8ghz processor.  I know the motherboard was made in 2002, but I don't remember the other specs.

Programs routinely freeze when running Rythmbox, Evolution, Firefox, and/or Chrome.  Yesterday, I had Rythmbox, Evolution, and Firefox running and everything froze.  I couldn't use my "force quit" button, alt+f2 wouldn't work, and I couldn't switch to another shell (ctrl+alt+f1-f6).  I did a hard reset which brought the line:

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

twice.  I finally did a hard shutdown and let it sit for 10 minutes, restarted and it restarted fine.

My husband is the hardware guy, I do software.  I know the HD is a 200GB IDE set in secondary, not primary.  The motherboard is a deluxe, and it talks to us telling us there is no floppy and telling us when it starts up.  

I want to know how to tell if we have hardware problems and what the 

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

really means, and if I should worry.

I've looked at the following posts and none seem to help:

[http://ubuntuforums.org/archive/index.php/t-455187.html](http://ubuntuforums.org/archive/index.php/t-455187.html)
[http://www.softwaretipsandtricks.com/forum/windows-xp/22178-disk-boot-failure-insert-system-disk-press-enter.html](http://www.softwaretipsandtricks.com/forum/windows-xp/22178-disk-boot-failure-insert-system-disk-press-enter.html)
[http://www.techspot.com/vb/topic26393.html](http://www.techspot.com/vb/topic26393.html)

Thanks in advance. :)

---

### Post by blueridgedog on 2009-12-24
> **lasleym said:**
> 

I want to know how to tell if we have hardware problems and what the 

DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER


The Bios of the motherboard is set to look in certain locations for a bootloader.  When it fails to see a bootloader in those locations, it gives you the message, which basically states that of all the places you told me to look, none seem to be bootable.  The fact that this goes away after you restart it a few times indicates an interment problem.

It could be that your hard disk is showing it's age, the connector is not seated or the controller on the motherboard is going bad (the hardware that manages the drive).  

As a test, I suggest you move the drive ribbon cable to another IDE port (I assume it is IDE).  

As far as the lockups...it is likely that they are related.  However, try booting on the LiveCD and running the memory test procedure.

---

### Post by lasleym on 2009-12-24
Thanks so much for the response.

The drive is 3 years old, and prior to being used to host the OS, it was just a secondary for music storage.  

What about the power supply?  Would it affect this type of problem?

---

### Post by blueridgedog on 2009-12-25
> **lasleym said:**
> 
What about the power supply?  Would it affect this type of problem?

Yes, but I would trouble shoot the other items first.  Checking the memory, then testing another hard drive port would be a cheap first step.

You can run Palimpset to look for errors on the dist (if you are running 9.10, it is included).  System -> Administration -> Disk Utility, select the disk, then "more information" and look for a reallocated sector count.

---

### Post by Bartender on 2009-12-25
Has the CMOS battery ever been changed?  Generally speaking you can expect to get about 5 or 6 years out of them.  If it's never been changed, you need to check that out.

While you're inside, blow out the cobwebs and take a careful look at the capacitors on the motherboard.  For more info on this visit [badcaps.net]("http://www.badcaps.net/").

A friend of mine was having intermittent problems with his PC.  It wouldn't recognize the HDD one day, the next day it seemed to be working OK again.  We found three blown caps on the motherboard.  We shipped the board to the badcaps guy and expect it will run like a champ when it's returned.

You can have bad capacitors inside the power supply, too.  Most people don't think of that.

---

### Post by lasleym on 2010-01-01
> **blueridgedog said:**
> You can run Palimpset to look for errors on the dist (if you are running 9.10, it is included).  System -> Administration -> Disk Utility, select the disk, then "more information" and look for a reallocated sector count.

Thanks, VERY MUCH, for this tip.  It said that the disk is healthy. And, we haven't had any lock-up issues since I uninstalled Compiz, and then rather just didn't set it up.

We have not pulled off the cover yet.  So I cannot comment on the other tips.  Although the need has grown more apparent with [video/driver issues]("http://ubuntuforums.org/showthread.php?t=1369217").  

Thanks also, for the Bad Cap suggestions.  We'll keep that in mind.

---

### Post by lasleym on 2010-01-01
> **Bartender said:**
> Has the CMOS battery ever been changed?  Generally speaking you can expect to get about 5 or 6 years out of them.  If it's never been changed, you need to check that out.
I don't know.  I know my father-in-law bought it off ebay.  I would imagine not.

---

