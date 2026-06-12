---
title: "Extend fsck log"
date: 2009-07-24
forum: General Help
---

### Post by CNLiberal on 2009-07-24
Two days ago, I had two drives drop off a RAID5 array with missing superblocks.  I was able to recover from the error.  When the array came back up, I ran an fsck_jfs on the array.  It found several files were corrupted.  I then rebooted the machine.  Well, the fsck log only stores the last fsck you do, so I can't remember exactly what files I need to replace from my backups.  Is there a way to make the logfile be something more than just the last fsck?  Like the last 10?  Thanks!

Jim

---

