---
title: "Files made in Ubuntu are erased by Windows?"
date: 2010-10-13
forum: General Help
---

### Post by flamefury on 2010-10-13
So I downloaded a bunch of study notes to my shared partition in Ubuntu.
When I logged in on Windows 7 though, they weren't there.
Logging back in Ubuntu also shows none of the study notes.


What are the possible causes of this?

---

### Post by DarthScape on 2010-10-13
Can you reproduce the issue? If you save some files there again, will they stay this time?

---

### Post by Mark Phelps on 2010-10-13
> **flamefury said:**
> What are the possible causes of this?

I'm presuming that "shared partition" was formatted NTFS (or was it FAT32) -- either way, the most common cause is something called unclean shutdown in which a "drive" (what we call a partition) is unmounted before a set of buffered writes can be completed.

This most often affects external drives (or USB sticks) when folks simply unplug them without "safely removing" them first.

But, it can also affect NTFS/FAT32 partitions that you automount through your FSTAB where writes are still taking place when you shutdown your machine -- which is why I advise folks to NOT automount NTFS partitions read-write.

---

### Post by flamefury on 2010-10-16
I don't automount the partition. I suspect it might have something to do with my usage of the sleep and hibernate functions.

Regardless, it looks like I should just be more careful when I choose my OS for the week.

---

### Post by psusi on 2010-10-16
> **Mark Phelps said:**
> 
But, it can also affect NTFS/FAT32 partitions that you automount through your FSTAB where writes are still taking place when you shutdown your machine -- which is why I advise folks to NOT automount NTFS partitions read-write.

No, when you shutdown ( properly, not by yanking the power cord or holding in the button until the immediate power off override kicks in ) all buffers are flushed.

---

### Post by flamefury on 2010-10-18
Well, I just verified why this happens.

I hibernate in Windows, next time I log on into Ubuntu and make a bunch of changes. The instant I log back into Windows, it'll go to what state it was in when I hibernated. Pretty obvious now that I think about it.

So yeah, all I need to do is be careful of when I hibernate.

Thanks for everyone's input.

---

