---
title: "Persistent Live USB Constantly Breaking"
date: 2011-12-01
forum: General Help
---

### Post by Panpandachan on 2011-12-01
Did a bit of google searching about this and didnt find an answer. I'll gladly be proven wrong lol.

Anyway

I've been running Ubuntu off of a USB for my laptop until I get a replacement HDD (previous one failed).

My issue is with running Live USB with persistence. It seems to break... a lot...

Break as in it hangs at start up. I do quiet start up and look at all the **** flying past the screen. Eventually it gets stuck on errors that look like "Deleted inode referenced"

Sorry I dont have the exact errors, I'm not next to another computer so I cant look at the errors and type at the same time.

Anyway, I ended up fixing it by editing out phrase "Persistence" in the USB boot menu. I did that, and it loaded.
So its definitely something wrong with persistence.
Also, I noticed that the system wont properly wake up from standby when I'm using persistence.

Help T_T

---

### Post by searchfgold6789 on 2011-12-01
This may be happening because of the failing hard disk. If you can provide more information about the error, I could probably make a better prediction on that :D

Try taking the hard disk out.
 - search

---

### Post by C.S.Cameron on 2011-12-01
Have you filled your persistence file, (casper-rw), perhaps by trying to to do an update or otherwise?

Do not try to update or upgrade a persistent install.

If you need the latest updates you can do a full install to flash drive  but will need at least an eight gig drive.

---

### Post by Panpandachan on 2011-12-01
If any updates were made, it wasnt me... I dont remember accepting any Ubuntu updates.

Been using a 4gb USB. Before that I was using a 8gb SD card w/ usb reader. Same issue with both.

Right now, I'm trying to just recover some files from casper-rw and then using a different Live USB tool to make the USB. Been using Universal USB Installer, gonna try LiLi now.

If that still breaks, I'll go back and get the errors.

---

### Post by C.S.Cameron on 2011-12-02
To mount casper-rw:

```
mount -o loop casper-rw-1000M /mnt/odd2fs/
```

---

### Post by oldtimer7777 on 2011-12-02
Persistent works as long as you allow it to completely boot down normally. If you rush the boot down in any way, like hard shutdown, and then a cold boot, you will break your Persistence each time that happens.  There are several other ways to break your persistence, and that is just the way it goes for now.  You have to be really careful with your persistent sticks of Ubuntu.  Power them down the old fashioned way each time you use them, and don't leave them in your computer long enough to go into hibernation/standby modes.  Disable them if you do, but use them sparingly.  Make duplicate USB live sticks.. I keep a few of them on hand always, in case one of them breaks..  etc etc..

> **Panpandachan said:**
> Did a bit of google searching about this and didnt find an answer. I'll gladly be proven wrong lol.

Anyway

I've been running Ubuntu off of a USB for my laptop until I get a replacement HDD (previous one failed).

My issue is with running Live USB with persistence. It seems to break... a lot...

Break as in it hangs at start up. I do quiet start up and look at all the **** flying past the screen. Eventually it gets stuck on errors that look like "Deleted inode referenced"

Sorry I dont have the exact errors, I'm not next to another computer so I cant look at the errors and type at the same time.

Anyway, I ended up fixing it by editing out phrase "Persistence" in the USB boot menu. I did that, and it loaded.
So its definitely something wrong with persistence.
Also, I noticed that the system wont properly wake up from standby when I'm using persistence.

Help T_T

---

