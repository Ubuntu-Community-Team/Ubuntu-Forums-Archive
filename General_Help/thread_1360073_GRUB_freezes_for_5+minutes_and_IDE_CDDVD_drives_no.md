---
title: "GRUB freezes for 5+minutes and IDE CD/DVD drives no longer work/detected."
date: 2009-12-20
forum: General Help
---

### Post by TheOnlyMrK on 2009-12-20
I had gotten my old first computer out and figured I'd mess with it and one of the first things I noticed was a warning on POST "No 80pin IDE cable detected on Primary IDE channel", after doing some searching on Google and finding out the differences between 40 and 80pin IDE cables I switched out the old and slow 40pin cable for an 80pin one that was in my other (main) computer because all that was plugged into it was a CD-RW drive and a DVD+RW drive so I figured they won't need a high speed 80pin IDE cable. After booting up my computer with the 40pin IDE I went to burn a CD to use to install Xubuntu on the other desktop but when I pressed the eject button on the front of the drive it didn't eject as if it was turned off because the status light on the drive didn't even blink meaning it's busy and can't open the tray right now, I went to "Computer" in the places menu to find that my CD and DVD drive weren't there.
So the next day I went to switch the IDE cables back to the same 80pin one (and later found another 80pin IDE so both my computers have nothing but 80pin IDE's now) but that didn't fix the problem and only made it worse, now right after "Loading GRUB..." appears on the screen the screen turns off for about a second then turns back on to a blinking _ cursor and stays like that for about five minutes before, I guess, giving up on something and moving on to finish booting.
The IDE cable works fine because I tested it back in the old computer with no problems and the BIOS POST detects the drives instantly along with I can see the drives during POST looking to see if they have a CD in them to boot from. I've tried unplugging one of the drives and leaving the other plugged in, checked the jumpers on the drives, made sure everything was plugged in completely, I can't find anything wrong.

Also one last note, I had remembered I had an Xubuntu 9.10 alternative install CD and put it in the computer then selected "Repair a broken system", while it was loading it kept repeating "ATA5: Device is slow to respond, please wait" every minute or so for once again about five minutes before it finally started, then I rebooted because I didn't want to go though all the reinstalling again.

---

### Post by dcstar on 2009-12-20
> **TheOnlyMrK said:**
> I had gotten my old first computer out and figured I'd mess with it and one of the first things I noticed was a warning on POST "No 80pin IDE cable detected on Primary IDE channel", after doing some searching on Google and finding out the differences between 40 and 80pin IDE cables I switched out the old and slow 40pin cable for an 80pin one that was in my other (main) computer because all that was plugged into it was a CD-RW drive and a DVD+RW drive so I figured they won't need a high speed 80pin IDE cable. After booting up my computer with the 40pin IDE I went to burn a CD to use to install Xubuntu on the other desktop but when I pressed the eject button on the front of the drive it didn't eject as if it was turned off because the status light on the drive didn't even blink meaning it's busy and can't open the tray right now, I went to "Computer" in the places menu to find that my CD and DVD drive weren't there.
So the next day I went to switch the IDE cables back to the same 80pin one (and later found another 80pin IDE so both my computers have nothing but 80pin IDE's now) but that didn't fix the problem and only made it worse, now right after "Loading GRUB..." appears on the screen the screen turns off for about a second then turns back on to a blinking _ cursor and stays like that for about five minutes before, I guess, giving up on something and moving on to finish booting.
The IDE cable works fine because I tested it back in the old computer with no problems and the BIOS POST detects the drives instantly along with I can see the drives during POST looking to see if they have a CD in them to boot from. I've tried unplugging one of the drives and leaving the other plugged in, checked the jumpers on the drives, made sure everything was plugged in completely, I can't find anything wrong.


Your BIOS should have a setting as to what cables you are using for the IDE devices.

---

### Post by TheOnlyMrK on 2009-12-20
> **dcstar said:**
> Your BIOS should have a setting as to what cables you are using for the IDE devices.

The only setting I have in BIOS for IDE is weather or not I want the IDE controller enabled.

---

### Post by Leppie on 2009-12-20
is there any settings for PIO mode or DMA? these are often found in other sections of the bios (so not where the disks are recognized and set).

---

### Post by TheOnlyMrK on 2009-12-20
> **Leppie said:**
> is there any settings for PIO mode or DMA? these are often found in other sections of the bios (so not where the disks are recognized and set).

Theirs DMA, I took some pictures of everything I could find that was IDE related. But I'm doubting this is a BIOS related problem.

---

### Post by TheOnlyMrK on 2010-01-02
After doing a complete rebuild of my computer so I could clean it out (Arizona dust + air cooled PC don't mix) I saw that one of the IDE pins on my motherboard was bent so I carefully moved it back in place and after reasembling my computer the CD drives work fine. I would of been able to notice this earlier if my motherboards IDE plug wasn't in such a weird spot; almost under the hard drive bay.

---

