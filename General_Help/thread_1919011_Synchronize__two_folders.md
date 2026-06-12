---
title: "Synchronize  two folders"
date: 2012-02-02
forum: General Help
---

### Post by kanishkdudeja on 2012-02-02
How can i syncrhonize two folders in Ubuntu?

So that if i add, delete or remove any files or folders within folder 1, then the same changes reflect back in folder 2.

Is this possible?

---

### Post by btindie on 2012-02-02
Yes, using rsync.
```
rsync -a --delete /tmp/src/ /tmp/dst/
```
which you'd have to manually run though you could put it in a script so you don't need to remember the details.

You can either have it run automatically every 1hr say from cron or using incron you can have it run when a file handle is closed on the file causing the sync to happen immediately.

users incrontab:
```
/tmp/a IN_CLOSE_WRITE /usr/local/bin/sync-script.sh
```
you can also get it to handle multiple events for when files are deleted.

---

### Post by kanishkdudeja on 2012-02-02
Thank you :)

---

