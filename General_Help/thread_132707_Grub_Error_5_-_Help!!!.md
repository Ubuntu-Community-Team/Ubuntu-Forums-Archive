---
title: "Grub Error 5 - Help!!!"
date: 2006-02-18
forum: General Help
---

### Post by mmcmonster on 2006-02-18
Hi.
  I was using partition magic under Windows to move a windows partition from hdb to hda, and now grub doesn't boot anything up.

I get an "error 5" in grub.

I'm currently booting off of a knoppix live CD, but don't know how to fix things up. :-(

hda1 is my windows c: drive and appears to be intact.
hdd5 is my windows d: drive and appears to be intact.
hdd6 is my Ubuntu /home mount point and appears to be intact.
I can't seem to find my Ubuntu / or /usr mount points. (They used to be on hda in a logical partition, according to partition magic.)

Where do I start?

---

### Post by dcstar on 2006-02-18
[QUOTE=mmcmonster]Hi.
  I was using partition magic under Windows to move a windows partition from hdb to hda, and now grub doesn't boot anything up.

I get an "error 5" in grub.

I'm currently booting off of a knoppix live CD, but don't know how to fix things up. :-(

hda1 is my windows c: drive and appears to be intact.
hdd5 is my windows d: drive and appears to be intact.
hdd6 is my Ubuntu /home mount point and appears to be intact.
I can't seem to find my Ubuntu / or /usr mount points. (They used to be on hda in a logical partition, according to partition magic.)

Where do I start?[/QUOTE]
Possibly Partition Magic has wiped out your Linux partition when you moved the Windows one to hda, unless you can see the Linux stuff in that utility then it may not be compatible with it.

You might be able to reinstall grub and have it fixed, do a forum search for this task.

---

