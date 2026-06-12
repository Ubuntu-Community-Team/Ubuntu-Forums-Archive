---
title: "Iso file size incorrect"
date: 2012-05-15
forum: General Help
---

### Post by captainKrash on 2012-05-15
Hi there,

I  have just installed 64 bit ubuntu desktop (12.04) and have subsequently downloaded the 32bit desktop iso for a friend. When the firefox download dialogue completes it shows file size of 701mb, however, the size on disk appears to be 735.4 MB (735,358,976 bytes) which will not fit on a standard CD.

Is there anything I am doing wrong or anything that I can do?

Thanks

---

### Post by Zvlwab on 2012-05-15
Firefox shows the filesize in MegaBytes (MB).
that can be calculated using the following formula:
735358976 / (2 ^ 10) = 701.29296875 MB

But Nautilus shows the filesize in MebiBytes (MiB).
This can be calculated using the formula:
735358976 / (1000 * 2) = 735.358976 MiB

So you're not doing anything wrong. You can't do anything but use another cd.
It seems the difference is just there to annoy people like you and me. :)

---

### Post by captainKrash on 2012-05-15
Ah ha. That explains it - thank you for taking the time, appreciated.

The fact that Brasero crashed was what got me flustered and concerned! I'll try burning another CD and see what happens.

---

### Post by sudodus on 2012-05-15
... or if the iso file is really oversized, burn a DVD (if your optical drive can manage that) or make a USB boot drive with Unetbootin or USB Disk Creator.

---

### Post by jmore9 on 2012-05-15
Most of the new iso's are over 700 but almost all fit on a cdr not a cdrw.  I always get the dvd version now because i only buy blank dvds no blank cds anymore.  Anything to small to fit on dvd will wait until enough gathered for full dvd or just make a iso and keep on hard drive.

---

### Post by cortman on 2012-05-15
Check the md5sum of the iso before you burn it too, to ascertain its integrity. Info on that [here.]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by captainKrash on 2012-05-15
> **cortman said:**
> Check the md5sum of the iso before you burn it too, to ascertain its integrity. Info on that [here.]("https://help.ubuntu.com/community/HowToMD5SUM")

I would if the md5sums were easy to find on the ubuntu website - I have search around the download area perhaps I am a bit blind?

CD burned successfully on second attempt, can only surmise that perhaps the machine was a bit overladen at the time.

---

### Post by captainKrash on 2012-05-15
Apologies found via your link!

d791352694374f1c478779f7f4447a3f  ubuntu-12.04-desktop-i386.iso

All good.

---

