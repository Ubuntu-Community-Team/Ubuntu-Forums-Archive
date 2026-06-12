---
title: "synchronizing backup directory"
date: 2010-01-29
forum: General Help
---

### Post by supersrbin2000 on 2010-01-29
Hi,

Can anyone please suggest me the best solution to the following problem:
1. i have two partitions for data
        - media/data_0, and
        - media/data_1
2. i make occasional changes on data_0 and use data_1 as a mirror/backup partition.

what i need to do is to find an elegant solution for synchronization of the contents between data_0 and data_1. ideally, it would be one console command which is able to check what's different and copy only those files that are modified. this should be done before each system shutdown at the end of the day, so it's desirable for it to be as fast as it can be in the given context.

currently, i'm considering rsync tool, but i'd like to hear more opinions and come up with the most optimal solution. thank you all in advance for your time and replies.

---

### Post by ajgreeny on 2010-01-29
I can't think of anything that would be better than rsync.  It is simple, effective for that job, and finally, it can be used with a crontab entry every day or hour, or as often as you want.

---

### Post by uncle-c on 2010-01-29
> **ajgreeny said:**
> I can't think of anything that would be better than rsync.  It is simple, effective for that job, and finally, it can be used with a crontab entry every day or hour, or as often as you want.

Ditto.

---

