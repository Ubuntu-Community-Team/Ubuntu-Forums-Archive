---
title: "hard disk problems"
date: 2010-11-24
forum: General Help
---

### Post by izar on 2010-11-24
i have a portable hdd with ntfs partition, i use it both in ubuntu and in windows.
recently it began giving me problems, and now it wont mount.
gparted tolled me to run "chkdsk /f" (under windows of course)

chkdsk shows that it fixes some file and on other files it says:
"insufficient disk space to recover data"
strange thing is the hdd has 150 GB free ](*,) 

any ideas?

---

### Post by pricetech on 2010-11-24
Can you read it in windows ??  If so, back up whatever is on it before you go any further.

Sound like you have a drive failing.  Check the manufacturer's website for their diagnostic and run it.

---

### Post by izar on 2010-11-25
thanks
i am cheking it out

---

### Post by izar on 2010-11-28
i emailed the company. they told me to format the drive.

i tried copying the drive using ddrecue. however i still cant mount the copied image or fix it. i tried also ntfsfix and ntfsresize (on the image) but gut error such as:```
Failed to read $MFTMirr: Input/output error.
ERROR(5): Opening 'Desktop/hdd/hdd2.ntfs' as NTFS failed: Input/output error
NTFS is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!

```
is there some way to restore my data or does this mean it is lost?

---

### Post by izar on 2010-12-04
am i already alowed to BUMP?

---

