---
title: "Most stable filesystem"
date: 2010-02-23
forum: General Help
---

### Post by lemurid on 2010-02-23
I'm building a home NAS Server. I have a separate RAID5 using 4 disks to host my Photos, Music and other speed irrelevant information. So the question is which filesystem to use on it? The one which has the most chances to withstand black outs, crashes, bad blocks e.t.c?

---

### Post by cpressland on 2010-02-23
For now I'd say the most stable FileSystem is EXT3 with EXT4 slowly maturing just behind.

---

### Post by lemurid on 2010-02-23
> **cpressland said:**
> For now I'd say the most stable FileSystem is EXT3 with EXT4 slowly maturing just behind.

Thanks. Ext3 than it will be. Last question. Journaling. Turn it on or off?

---

### Post by cpressland on 2010-02-23
In case of a crash or powerfailure Journaling is there to get the system repaired and back to a stable state as quickly as possible. Personally, I always leave it on, unless you're doing nightly backups.

---

