---
title: "NTFS to ext PRESERVING file dates"
date: 2009-09-25
forum: General Help
---

### Post by Lockheed on 2009-09-25
I need to convert 200GB NTFS data partition to ext3 or ext4 or ReiserFS (btw, which is best?).

What I need is the method that will allow me to preserve **dates of file creation**. If I just copy them over, the dates will reset.
This one thing is crucial to me.

Is there such method?

---

### Post by geirha on 2009-09-25
Try grsync: [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

---

### Post by Lockheed on 2009-09-25
Thanks, I'll look into it.
How about "-p" parameter of command "cp"? Would that do the trick?

---

### Post by StuartN on 2009-09-25
> **Lockheed said:**
> I need to convert 200GB NTFS data partition to ext3 or ext4 or ReiserFS (btw, which is best?).

This is a bug caused by the way that the NTFS volume has been mounted with root ownership - just use cp in the command line to see the error message saying that you don't have permission and the change of permissions fails. Copying from NTFS seems unaffected. Either:

1. Mount the drive manually with option uid=Lockheed

2. Use rsync / grsync, which is not affected

---

