---
title: "USB stick automounting in read only"
date: 2009-12-16
forum: General Help
---

### Post by alegallo on 2009-12-16
I have recently installed Karmic Koala in my new pc, and it started to have a strange behaviour with my Kingston 8Gb USB stick.

I use the 64bit version on my Athlon II X4, motherboard ALiveNF7G-GLAN, 2Gb RAM, and installed pysdm to have my other HD partitions (Windows and data, both NTFS) automounted on boot.
Honestly I did not check if the stick worked before, or I just don't remember. Sorry!

I managed to get the automount without any problem, and I did it without having my usb stick plugged in.
After that I wanted to transfer some files to my USB stick, which was automounted but in read only mode.

The weird thing is that I could copy ONE single file on it, after which it became read only.

I tried to check what happened, and I could just enable rw using pysdm, which implies having a permanent /media/KINGSTON folder, where the stick will be mounted after plugging it in.

This workaround worked for some reboots, but I got the same problem again after 2-3 days.

I really don't know what to do: I have to boot every time in win when I need to use my USB stick.

Any hint/idea of what may be wrong? :(

---

### Post by prshah on 2009-12-16
> **alegallo said:**
> The weird thing is that I could copy ONE single file on it, after which it became read only.

Any hint/idea of what may be wrong? :(

Looks to me like a "dirty" filesystem; eg, when using Windows or Ubuntu, the stick was probably removed without the "Safely Remove" option, or without unmounting first.

There is a way to confirm. Open a terminal (Applications-Accessories-Terminal) and give the command```
tail -f /var/log/messages
``` Now plug in the USB stick. You should notice a whole bunch of new lines in the terminal. Please wait about 10 seconds, then copy and post the output here for clues to what the problem may be.

---

### Post by alegallo on 2009-12-16
Thank you prshah, I will be able to do it later in the evening.
Now it's morning in Italy and I'm at work ;)

Anyway, I always unplug the stick safely, so I think that the "dirty" filesystem option should not be the one ;)

I am afraid of a confusion between SATA and USB: it would seem from pysdm that the two interfaces get crossed.
It's difficult to explain without my pc in front of me, I'll post a screenshot tonight ;)

I did not say that the filesystem is FAT32

---

### Post by t0p on 2009-12-16
I've experienced this problem, and it's meant that the filesystem was corrupted or otherwise 'broken'.  Reformatting may sort it.  But the stick might be physically damaged, in which case replacement is the order of the day.  If I haven't had the stick more than 12 months or so I always get a free replacement or a refund.

I'm not saying *your* stick is corrupted/broken.   Just pointing out a possibility.

---

### Post by alegallo on 2009-12-16
I was probably wrong about broken FS, and you all right ;)

I checked the USB pen here at work (Win XP) and saw that one folder with mp3 files was taking up 59Gb in a 8Gb filesystem :tongue:

I just re-formatted it, and later I'll try it in my home pc. 

I'll keep in touch, maybe in a couple of hours (maybe I'm going home for lunch ;) )

---

### Post by prshah on 2009-12-16
> **alegallo said:**
> I am afraid of a confusion between SATA and USB: it would seem from pysdm that the two interfaces get crossed.

When you hear hooves, think of horses, not zebras :D 

> **alegallo said:**
> 
I just re-formatted it, and later I'll try it in my home pc. 

Should be OK; please remember to unmount/eject/safely remove before physically removing the stick.

For the future, please remember that running a chkdsk on the stick is an option that should be tried _before_ formatting; formatting should be used only as a last resort. (Or that's my opinion, anyway :) )

---

### Post by alegallo on 2009-12-16
prshah and t0p, you were both right! 

The fs was really broken, and I solved everything after re-formatting.

To be honest, I didn't even think about a dirty filesystem, because the stick was read perfectly in win and also recognised in Ubuntu, so I guessed there was a problem with permissions.

Ever since I have a USB pen I remove it safely, both under Linux and Win (I know it provides a longer life to the stick), but I reminded that there was a power fault some time ago, when my stick was plugged in. 
Probably it was the reason for the data corruption.

It were your hints that made me check more carefully, so thanks a lot for your great help \\:D/

(P.S.: I made a mental note for chkdsk too. I used to run it under DOS once ... too much GUI now! ;) )

---

