---
title: "mdadm Help"
date: 2010-09-08
forum: General Help
---

### Post by Go3Team on 2010-09-08
I added another drive to my RAID6 array the other day, and as soon as I hit the enter button to issue the command to grow the array, the system crashed.  I had no choice but to reboot.  After the reboot, the system tried recovering the raid, and kicked out just enough drives to have a degraded array.  When the RAID finished doing whatever it was doing 36 hours later, it started to grow to back to the drives it kicked out.  Shortly thereafter, mdadm reported a faulty drive, and now it won't come back up.  

I've checked the SMART data on all 14 drives and they all seem ok. 

I've tried removing/purging mdadm to reset the mdadm.conf file, and it seems that it still sees the old raid as it was.  I've looked around some, and I can't find a way to tell the RAID that the drive it kicked out is indeed good and to take it back.

I've read about zeroing super blocks, but without knowing what that does exactly, I'm not going to do that.

I have around 10TB of stuff on the RAID, so I'm pretty annoyed this is happening, and don't want to chance loosing it, if at all possible.

Many thanks to whoever can help out.

---

