---
title: "Access to partitions through Terminal problem"
date: 2011-05-05
forum: General Help
---

### Post by alextsl on 2011-05-05
Hello, I am totally new to Linux and I have an issue accessing the Local Disk.
I deleted the Windows partition, created all I needed to, installed 11.04 and left the other 2 partitions untouched(they are NTFS). For some reason, I can't access these partitions through the Terminal. They are named Local Disk and Local Disk_ but when i try to enter them by Terminal it says that there is no such directory. Am I doing something wrong?

---

### Post by ~Plue on 2011-05-05
Since the directory name has spaces, you should escape those spaces or put the path in quotes;
```
cd /media/Local\ Disk
cd '/media/Local Disk'
```

---

### Post by alextsl on 2011-05-05
Thank you, that worked.

---

