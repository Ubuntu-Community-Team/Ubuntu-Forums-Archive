---
title: "Incorrect Date Modified when mounting SD Memory Card via USB Card Reader"
date: 2009-09-10
forum: General Help
---

### Post by the_arm on 2009-09-10
Hi there - I'm hoping someone can help me out with this!  I'm currently running Ubuntu 9.04.  I live in Minneapolis which is currently 5 hours earlier than GMT.  I have my time zone set correctly and the current time displays correctly on my desktop.  

Anyway, my problem isn't with the clock, per se:

Here's my problem:
Whenever I put my USB-based SD memory card into my card reader, the files that are on that SD card have the incorrect Date Modified both in Nautilus and on the command line...they are all 5 hours earlier than they should be.  It's as if the Ubuntu box is mounting the SD card as if all the files were GMT, and then subtracting off the 5 hours to display it in Central Daylight Time, where I'm at.

I've verified this with 2 FAT32 formatted cards and a FAT formatted card...on jpegs taken from 2 different cameras and from wavs taken from my Zoom H2 audio recorder.  The times are set correctly on both cameras and audio recorder...and in fact the time zone is set correctly on my nicer camera (Nikon D5000), but the point and shoot camera and the Zoom only have time, not time zone.

The kicker is when I take the same card reader and stick it in my Windows laptop, the Date Modified is correct.  So I know I'm not crazy.

So, to be specific, if I take a photo or record a .wav or .mp3 at 7pm here and remove the SD Card and put it in my card reader, when it mounts in Ubuntu it will have a Date Modified of 2pm (as it must be assuming that it was created at 7pm GMT).  If I take the card reader and put it in my Windows box it has the correct date modified time of local 7pm.

I'm not sure where to start with this -- is there a way to tell Ubuntu to (auto) mount these cards as if they were taken in my LOCAL time zone?

thanks!
-arm

---

### Post by the_arm on 2009-09-11
Hmmm...so at least I know I'm not alone:

[http://ubuntuforums.org/showthread.php?t=1190856](http://ubuntuforums.org/showthread.php?t=1190856)

Looks like this individual was having the same issue too, without resolution.

Anyone else have this problem? I don't like the idea of setting my devices all to UTC just to operate with Ubuntu because then the files will be messed up everywhere else.

I know for the .jpgs at least I can do a mass update using jhead, but for other files it's not as elegant.

I'd just like my Ubuntu box to assume that the files that I'm mounting on my SD card were taken in local time not GMT/UTC.

Thanks!
-arm

---

### Post by dcstar on 2009-09-12
> **the_arm said:**
> 
........
The kicker is when I take the same card reader and stick it in my Windows laptop, the Date Modified is correct.  So I know I'm not crazy.
.......

All that may mean is that the Windows box is not set up in the correct time zone.

All underlying file timestamps should be in in UTC, and the local OS should be also set up correctly to display any Local Date/Time correctly using this base data.

---

### Post by the_arm on 2009-09-12
thanks for the reply -- I guess I should have mentioned that.  The windows box is also configured appropriately for the right time zone.  In fact, out of curiosity I put the same card reader in my girlfriend's windows laptop and it also displays the time modified correctly (and it ALSO has the timezone set properly).  The windows boxes are behaving as expected.

The only offender is my ubuntu box, which seems to assume that any card (FAT, FAT32 I've tried so far) I stick in it that the date modified on it was created UTC instead of in my local timezone...which for me makes it appear as if everything was created 5 hours earlier than it actually was.

thanks though!
-arm

---

