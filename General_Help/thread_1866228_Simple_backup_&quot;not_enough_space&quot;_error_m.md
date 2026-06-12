---
title: "Simple backup &quot;not enough space&quot; error message wrong"
date: 2011-10-21
forum: General Help
---

### Post by rdh61 on 2011-10-21
Hi,

Simple backup has recently started telling me...

"Not enough free space in the target directory for the planned backup (free: 3422 MiB 568 KiB, required: 11857 MiB 659 KiB 451)."

This is wrong. I have 75 GB free space on the disc where the target directory is located. I get the same message if I change the target directory from the internal HD to an external one. Both have loads of space.

Any ideas?

Many thanks.

---

### Post by rdh61 on 2011-10-22
Also, Brasero Disc Burner is telling me:

"The location you chose to store the temporary image on does not have enough free space for the disc image (104 MiB needed).
You may want to free some space on the disc and retry."

---

### Post by dcstar on 2011-10-22
> **rdh61 said:**
> Hi,

Simple backup has recently started telling me...

"Not enough free space in the target directory for the planned backup (free: 3422 MiB 568 KiB, required: 11857 MiB 659 KiB 451)."

This is wrong. I have 75 GB free space on the disc where the target directory is located. I get the same message if I change the target directory from the internal HD to an external one. Both have loads of space.

Any ideas?

Many thanks.

Let me guess, you are using FAT32 partitions?

---

### Post by rdh61 on 2011-10-24
Only in my brain. The answer, I fear, is the old one... human error. Actually I didn't have enough space. Duh...
On my internal HD at least. Still cannot work out why when I tried to backup onto my external HD (where there IS loads of space... no, really), I got the same message. 
But it's all working now, so I'll mark as solved.

---

### Post by rdh61 on 2011-10-31
Alas, this wasn't the end, but it turns out I wasn't being entirely stupid. The problem came back, and eventually I found out that Simple Backup had left tens of backups in /root/.local/share/Trash. I found the solution here:

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

