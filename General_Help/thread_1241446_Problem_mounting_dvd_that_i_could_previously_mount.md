---
title: "Problem mounting dvd that i could previously mount"
date: 2009-08-16
forum: General Help
---

### Post by blackmech141 on 2009-08-16
background: 
I installed xbmc on top of a minimal ubuntu installation about 1 week ago.  After a reboot, the dvd i was just watching would not mount.  I ignored the problem .. then it happened again with another disk.  Thinking it was user error, i was messing with configs a lot, I wiped the box and started over.  

Now, a completely different dvd will not mount (rebooting server did not help). This problem seems to be triggered when my box locks up and I reboot it.  As for the dvds that would not mount after my first install..they work fine now. Which proves to me that this problem is not related to the dvd or dvd reader/cdrom dive or how I'm mounting these dvd's.

When I mount via command line with the dvd that does not work:


[SIZE="2"][B]#sudo mount /dev/scd0 /media/cdrom -t udf
**mount: no medium found on /dev/sr0**[/B][/SIZE]

So here is what I know FOR SURE:
1. My dvd drive is NOT defective .. I can read all other dvd's
2. My dvd is NOT defective
3. I am mounting it correctly and there is NOTHING wrong with my fstab


I'm wondering if mount or udf keeps some type of metadata or dvd specific information somewhere - and that file got messed up??????

---

