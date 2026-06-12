---
title: "External USB Harddrive not working in Ununtu!"
date: 2011-05-06
forum: General Help
---

### Post by branko.savic on 2011-05-06
I have a WD elements 1TB external harddrive that is formated in windows 7 as an NTFS disk, it works perfectly in windows, but when trying to connect it in ubuntu I get the following error:

Error mounting: mount exited with exit code 12: Failed to read last sector (1953523119): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Any help to fix this would be greatly appreciated!

---

### Post by branko.savic on 2011-05-06
anyone?

---

### Post by Quackers on 2011-05-06
Is the drive brand new or did it come from a different computer - possibly one using raid?

---

### Post by branko.savic on 2011-05-06
> **Quackers said:**
> Is the drive brand new or did it come from a different computer - possibly one using raid?

It is not brand new, have been using it when I had windows 7, and it is a netbook, so no raid!

---

### Post by branko.savic on 2011-05-07
Any idea how I can get this going?

I have some valuable files in the harddrive so I dont want to format if I can avoid it!

---

### Post by olwe on 2011-05-13
I got this same sort of error with my external drive. I think it happened because I jerked the cable out before it was through with a copy. Anyway, I tried it on another Ubuntu machine -- same error. Tried it in a Win7 machine and it sees it; however, the directory I was copying seems somehow corrupted. I'm running Win7 Tools/Error Checking now. This supposedly does "automatically fix file system errors" and "scan for and attempt recovery of bad sectors". Gotta go. I'll tell you if I've had any luck.

---

### Post by olwe on 2011-05-13
Okay, back now. Yes, after a lengthy Win7 tools error check/correct, it fixed the problem. I then deleted the "problem" directroy, unmounted, plugged it into Ubuntu -- and it made sickly beeping noises. Unplugged it, stuck it back in Win7 machine. Still works fine. Unmounted, plugged into Ubu machine -- works... Hope this helps.

---

