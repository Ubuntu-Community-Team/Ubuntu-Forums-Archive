---
title: "Accidentally Suspend During Gparted's NTFS Resize (Shrink)"
date: 2009-11-10
forum: General Help
---

### Post by Musafir_86 on 2009-11-10
Hi all,

-I've been using Ubuntu since 2006, but just registered here in this forum today. :P

-My problem: GParted (from Karmic Final LiveCD) was in the middle of resizing a NTFS partition (shrinking and moving data) when I *accidentally* suspended the laptop by closing the lid. Trying to resume back resulting in crash/freeze/lock-up. So, I had to hard-reset the system.

-IIRC, closing the lid in Jaunty LiveCD would only turn off the LCD, not suspending the system.

-During the next boot (Windows XP SP3), CHKDSK ran automatically and found lot of inconsistencies (too many messages, such as "*Deleting an index entry with Id xxxx from index $SII of file xxxxx.*" and "*Replacing invalid security id with           default security id for file xxxxxx.*"). I waited until it finished checking and rebooted. After that, I found that the volume size is already shrunk to target size (even though GParted hadn't had it finished yet).

-Then, when I checked the volume, I didn't find anything like "FOUND.00x" folders that usually contain orphaned files. So, I think everything is okay until I began encountering unreadable files! **There're a lot of garbled DOC, RTF, and TXT files, invalid JPG and MP3 files, and other formats which also corrupted.**

-My questions:

(1) Do this really caused by the crash/freeze (from the accidental suspend)?

(2) Do ntfsresize (which is used by GParted) update the NTFS filesystem progressively as it moves the data from the beginning of the partition to end? Or it'll do that after finished moving everything? Will the crash resulting corruption in already moved files? I know that the current files being moved are mostly damaged anyway.


Regards,
-Musafir_86.


P/S: I just want to confirm, AFAIK ntfsresize is pretty data-safe so maybe this wasn't caused by it. The laptop is my friend's, not mine, and it could be those files *were already corrupted* before I get my hands on it (I don't dare to tell about it). 8-[

---

### Post by Giblet5 on 2009-11-10
It should have resumed moving the filesystem. Whether you could see what was going on or not (most PCs have disk activity indicators these days = when that light is blinking/flickering/etc, the system is not hung even if you can't do/see anything on the screen). If you lost data, it's most likely because you power-cycled the system w/o checking for activity first.

Suspend is buggy on every OS but Mac AFAIK. Win XP is the worst.

How certain are you that the partition was uncorrupted when you started resizing it?

When did you last do a backup of that partition? Now seems a good time to begin the restore.

---

### Post by Musafir_86 on 2009-11-10
> **Giblet5 said:**
> It should have resumed moving the filesystem. Whether you could see what was going on or not (most PCs have disk activity indicators these days = when that light is blinking/flickering/etc, the system is not hung even if you can't do/see anything on the screen). If you lost data, it's most likely because you power-cycled the system w/o checking for activity first.

Suspend is buggy on every OS but Mac AFAIK. Win XP is the worst.

How certain are you that the partition was uncorrupted when you started resizing it?

When did you last do a backup of that partition? Now seems a good time to begin the restore.

-Thanks for replying.

-Yes, this system (Hyundai M-Life MYM547SE; a rebranded CLEVO model) is proven unable to resume from suspend (tested after a fresh install of Karmic into HDD). The CAPS LOCK etc aren't responding, and the LCD screen is garbled (nothing on screen; only backlight).

-This machine could be suspend/standby and resumed back successfully on Windows XP SP3, though.

-Yes, it's fine as I ran a CHKDSK /R first before doing the resize.

-Backup? Err, none, as I thought nothing would happen during the resizing operation (it has battery after all). Pretty bad of me indeed...

-Any clue?


Regards,
-Musafir_86.

---

### Post by Giblet5 on 2009-11-10
My laptop resumes well from everything but Vista. My wife's does Vista great but won't resume in XP... Go figure.

I'm afraid that this is the point where you must begin to accept that some/most/all of your data on that partition is gone or corrupted. Sorry for the bad news.

You can check each file. And you probably should. But I suspect it will be a disappointing activity.

Resizing a partition is never a trivial task. I'm pretty sure that every scrap of documentation, for every partition-resizer, includes bold text warnings about the potential for data loss.

External USB disks are very inexpensive now - certainly cheaper than all of the time it took to collect all of that data.

I keep a 1TB USB disk beside each computer and everything gets backed up to it while I sleep.

---

