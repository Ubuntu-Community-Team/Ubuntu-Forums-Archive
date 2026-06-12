---
title: "Hard drive disk errors"
date: 2012-02-20
forum: General Help
---

### Post by jesushero on 2012-02-20
I had some problems with one of my main work computers that have left me a bit puzzled.

It started when a CRT monitor that had been sitting unused for a year or so fried my graphics card upon being connected. After replacing the graphics card and connecting a safe monitor, the computer would not boot because of read errors on sda1, a WD 500 GB ATA drive, less than 2 years old. 

After a few attempts it booted command-line only, as the x server would not start. I tried a self test with smartctl which would not finish because or read errors. Then on the next reboot fsck did the scheduled test and came up with problems that had to be fixed manually. I spent a few hours reallocating bad sectors and correcting inode weirdnesses, and eventually it worked. Booted up properly. However, the smartctl selftests still don't pass. Still the same read errors. Some data loss has occured (not much) due to the shuffling around of bad sectors, but in general the system works fine now.

Are the read errors something on the software layer (ie something that will go away completely if I format the drive and start again), or is it on the hardware layer (ie the drive is failing and I should toss it out the window and get a new one)?

There's none of the usual noises that accompany a failing drive. Why would the self-tests still come up with read errors when the rest of the system works perfect, with read-write operations working perfect?

I'd rather not format the drive because this computer has no internet access and has a bunch of fine-tuned software that would be a pain to re-adjust and re-compile. Any pointers?

---

### Post by gordintoronto on 2012-02-20
Do you have Disk Utility installed? In older versions of Ubuntu it appears under Administration. It lets you click on a drive and display the SMART status.

That said, I think you should ensure you have complete backup before doing anything else, because I think this drive will soon be toast.

---

### Post by sudodus on 2012-02-20
We cannot be sure why your computer started failing.

If your assumption is correct, you fried your graphics card. Maybe you shut down your computer in a bad way after that, which caused the damage on the hard disk drive. Usually such damages are only logical (no [physically] bad sectors). But in your case maybe the pickup hit the disk and caused a damage. If this is the case, it might be a single damaging event, and the disk might continue to run for years, but you cannot be sure. So make a clone with ***ddrescue*** or at least ***backup*** your private files. The info page is very well written
```
info ddrescue
```

I guess you have tested that the old card is really fried, now that the computer works again (tested with a safe monitor). Otherwise do that, because it might have been a disk error, that corrupted the video driver and made you think the card was fried. (I admit it is not very likely, but unlikely things happen.)

Anyway, I think smartctl read errors means that there are bad sectors, physical damage to the disk. So as suggested by *gordintoronto*, try with the Disk Utility alias ```
palimpsest
``` Install if necessary with ```
sudo apt-get install gnome-disk-utility
```

---

### Post by jesushero on 2012-03-06
So the problem was that the MBR had become corrupt, making the disk think that there's bad sectors. It couldn't be repaired until the MBR (and the entire disk) was completely empty (I zeroed it out) and then SMART scanned like that. Smart reported it clean. I then proceeded to reformat and repartition, and re-use for the same data (that I had backed up elsewhere), and it still works fine now. 

Thanks everyone!

---

