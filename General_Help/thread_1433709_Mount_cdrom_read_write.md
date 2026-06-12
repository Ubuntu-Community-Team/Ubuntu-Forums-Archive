---
title: "Mount cdrom read write"
date: 2010-03-19
forum: General Help
---

### Post by cjhabs on 2010-03-19
Hi

I am running Karmic x64 on a HP laptop that has a cd/dvd burner.
I have a r/w cd with files on it and I wish to add/remove files to it.
After it mounts automatically on insertion, I unmount it and remount with:
sudo mount /dev/sr0 -t iso9660 -w /media/cdrom
(I tried assorted other hare-brained things also)
but it always says that the filesystem is read only.
Do I need to use a different device than sr0? Is it even possible under Ubuntu?

Thanks in advance

Chris

---

### Post by cjhabs on 2010-03-19
> **cjhabs said:**
> Hi

I am running Karmic x64 on a HP laptop that has a cd/dvd burner.
I have a r/w cd with files on it and I wish to add/remove files to it.
After it mounts automatically on insertion, I unmount it and remount with:
sudo mount /dev/sr0 -t iso9660 -w /media/cdrom
(I tried assorted other hare-brained things also)
but it always says that the filesystem is read only.
Do I need to use a different device than sr0? Is it even possible under Ubuntu?

Thanks in advance

Chris

OK - so to make a long story long - I have resolved the issue, but there really wasn't an issue.

I was trying to write more files to the cd and to remove some files. They way the cd had been created was preventing that - it was done using Toast on a mac.

I couldn't write to it under windows either.

By right clicking on the mounted icon I could clean the disk and start afresh and then I was able to write to the cd simply by dragging and dropping - the system recognized it as a rw cd and Brasero did the job of burning to it.

There is probably a way of writing it in multi-session mode which would allow appending but I don't really care enough to investigate it.

Thumbs up to Ubuntu!

---

