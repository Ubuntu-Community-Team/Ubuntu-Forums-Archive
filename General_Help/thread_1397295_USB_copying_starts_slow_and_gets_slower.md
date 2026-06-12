---
title: "USB copying starts slow and gets slower"
date: 2010-02-03
forum: General Help
---

### Post by everytimeref on 2010-02-03
I know there were threads on USB problems already, but there does not yet appear to be a definitive solution to USB speed problems on Karmic.

flash drives are very slow to copy to. running lsusb in terminal, it appears to be running at USB 1.1 speeds, but even that doesn't seem to be the whole picture. When I copy an 800mb file to the drive the first 150mb transfer in a matter of seconds, then the mb/s seems to get slower and slower, starting at about 12 and ending at about 5. If I copy multiple files to the USB at the same time the problem seems to get even worse, taking about 10 minutes to copy 1600 m/b - less than 1 mb/second.

copying files to other USB devices (card-reader and phone) is similarly torturous.

---

### Post by LoneWolfJack on 2010-02-03
you won't get much more than 5 mb/s out of cheap USB flash drives. check your hardware what the vendor says about write speed.

second, if you transfer many files, there's a lot of protocol overhead which further reduces the actual write speed.

---

### Post by ajgreeny on 2010-02-03
How about transfer from the usb drive?

The speed often comes down to the restriction of write speed on the drive itself rather than anything to do with the usb system transfer speeds, though that will certainly have some effect.  Try a known fast, new usb drive and you may find a big difference.

---

### Post by Grenage on 2010-02-03
While I do usually get USB2 speeds to my keyrings (5MB/s), a _lot_ of devices still often connect at USB1.1 speed, which as you now know is about 1MB/s - and painful.  Reconnecting the device often sorts it out, but I've not found a cure.

---

### Post by everytimeref on 2010-02-03
Thanks for the replies all, I'll test the 'copy to' speed as well tonight and test the speed using the same hardware on [SIZE="1"]windows [/SIZE]another operating system

---

### Post by everytimeref on 2010-02-04
FWIW,

I tried the same drive on far superior hardware (my work PC: quad core xeon workstation) running windows 7 and got transfer rates starting at 6 MB and falling to 2.5.

It seems the drive is just rubbish.

---

### Post by Grenage on 2010-02-04
I am guessing that the start transfer speed is never really reached; it probably does a burst write and then averages down.  Kind of like how IE downloads used to start at 800Kb/s then drop down to a 5.5Kb/s (ah, modem days).

---

