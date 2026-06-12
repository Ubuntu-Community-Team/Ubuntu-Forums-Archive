---
title: "Interesting Irregularities in Write Speeds"
date: 2012-03-20
forum: General Help
---

### Post by SeanTater on 2012-03-20
**The Intro**
I'm using my computer as a VDR/DVR using, shockingly -- VDR. But in order to record video reliably, you need to be able to write it at a good clip (5-10 MB/s preferably). I've been writing to my RAID1 setup quite successfully at speeds of about 50-60 MB/s with occasional peaks above that so I have plenty of room for error.

**The Problem**
I am inching closer to full on my drive. Right now it is at 84% full of 2TB (286GB left). I would expect that it would slow down as it searches for contiguous regions to write.
I did a full backup as a reflex, and I even reformatted my drive, switching from BTRFS to EXT4 since I think EXT4 is a bit less experimental but should not be terribly slow either. Then I wrote the backups back on the drive.

**The Interesting Part**
Around 40% full it started acting up again. Files would write in excess of 120MB/s as though a cache was filling (but the files were huge, >10GB) and then the next file would write extraordinarily slowly. Even as slow as 600 **KB**/s. After the backups were done (since that was my biggest concern) I ran this so that I would get an idea what was going on:
```
$ dd if=/dev/zero bs=1048576 count=1024 of=/media/brian/writespeed
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB) copied, 0.795037 s, 1.4 GB/s

```
1.4 **gigabytes** per second! The command returned almost instantly and the whole filesystem became unresponsive.
[font="monospace"]ls -lh /media/brian/[/font] took upwards of two minutes.
I had [font="monospace"]iostat -mxd 3[/font] running at the same time as [font="monospace"]dd[/font] and [font="monospace"]ls[/font]. (the result since scrolled out of the terminal history) It showed that the average wait for a call skyrocketed, to as much as ten or fifteen seconds per call!

**The Plea**
What hideous bug or "undocumented feature" is causing this? Is this really how a full filesystem is expected to slow down, even at only 40% fill??

---

### Post by dcstar on 2012-03-22
> **SeanTater said:**
> 
.........
**The Plea**
What hideous bug or "undocumented feature" is causing this? Is this really how a full filesystem is expected to slow down, even at only 40% fill??

Get a drive that doesn't have borderline bad blocks that cause massive slowdowns as the retries eventually push through and see how that goes.

---

