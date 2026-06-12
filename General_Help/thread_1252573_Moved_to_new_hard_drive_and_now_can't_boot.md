---
title: "Moved to new hard drive and now can't boot"
date: 2009-08-29
forum: General Help
---

### Post by manekineko2 on 2009-08-29
I have my Ubuntu system files on my primary hard drive, and then my home partition and swap partition on a secondary hard drive.  I recently upgraded my secondary hard drive, and used gparted to re-establish the partitions on the new hard drive, and then manually copied everything over.  I modified my fstab to stop using UUID's and to point simply to /dev/sdb#.

However, after I did all this, now when I start up all I get is a black screen with the mouse cursor, and no other feedback whatsoever on what the problem is.  Does anyone have any idea on what type of problem would cause this and if not does anyone have any suggestions on how to debug?

---

### Post by manekineko2 on 2009-08-29
Got this one figured out in case anyone else has a similar issue.

Problem was in my fstab file, I still had a leftover mount that I had missed.

A pretty gruesome error given the lack of errors or feedback, which is something that could really use some improvement.

---

