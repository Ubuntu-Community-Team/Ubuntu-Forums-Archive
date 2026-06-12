---
title: "usb problem"
date: 2009-12-08
forum: General Help
---

### Post by jimmys_ on 2009-12-08
Hello.
A few days ago I plugged a usb stick into a laptop with ubuntu 9.10. When I finished I chose Safely Remove and then unplugged the usb. Since then, my usb is broken. When I tried to plug it again the usb's light goes on and then immediately off and the usb is not recognized. I have tried plugging it on a windows system and only every 1 out of 20 tries seems to recognize it.
Was this just a coincidence(the usb just broke) or is there something else wrong?
Thank you.

---

### Post by akashiraffee on 2009-12-08
> **jimmys_ said:**
> 
Was this just a coincidence(the usb just broke) or is there something else wrong?
Thank you.

Probably, I've used usb keys in linux almost daily for years and never had one bust.  In fact the first one I ever bought still works, and has never needed reformatting.  They are pretty hardy devices -- last week one went thru the washer AND dryer, both on hot, and it seems fine.

But nothing is perfect.  It sounds like you might as well kiss the data goodbye.  I would try reformatting it in windows if you know how.

If you can remember what drive assignment it usually got (sdb1, etc), you could try badblocks on it (qv. man badblocks).  I usually do this when I get a key new, before I reformat it ext2 (do not format usb keys ext3 or ext4).

If you want to use the key in windows and linux, format it in windows -- you can still do a badblocks first in linux.  badblocks -w, which is a thorough test (but it overwrites all data and destroys the filesystem), takes about 5-10 minutes per Gb.

If the drive was, eg, sdb1, try both /dev/sdb1 and /dev/sdb.  Just make sure there are no other drives associated with sdb!

If none of this works, throw the key out.  Sorry.

---

