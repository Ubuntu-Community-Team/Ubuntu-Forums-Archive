---
title: "Hard drive usage not freed after deleting a file"
date: 2010-03-11
forum: General Help
---

### Post by mikerobinson on 2010-03-11
I just deleted a 10GB file that was in my /home/ partition, however I see now that the file is not there, however the space has not been freed on that partition.

> sudo du -hs /home
47G     /home

> $ df -h | grep sda6
/dev/sda6              61G   57G  1.8G  98% /home

What on earth could be causing this? It would be nice to recover those 10GB.

---

### Post by srs5694 on 2010-03-11
First, how did you delete the file? If you did it in a GUI by dragging it to a trash icon, you may just need to empty the trash.

Second, some filesystems are slow to delete big files. It could be that your system is still digesting the file, and the freed space will appear soon.

Finally, some filesystems (but not ext2/ext3/ext4, which are common with Ubuntu) automatically keep "snapshots" of disk state and so don't fully delete files for some time, if at all. I doubt if this is the case for you, but it might be if you're using an unusual filesystem.

---

### Post by mikerobinson on 2010-03-11
I deleted the file in konqueror with shift-delete. If it was in the trash it would show up in df.

> Second, some filesystems are slow to delete big filesI've never heard of this, however even still, the file was deleted probably 2 hours ago and the free space still hasn't appeared.

Finally, my filesystem is ext3

---

### Post by mikerobinson on 2010-03-12
OK I rebooted and I now have the 10 gigs back. Sounds like a bug to me.

---

### Post by nemilar on 2010-03-12
The most common cause of this is that something is still holding the file open.  Since you rebooted and the space "came back," I would bet that this is the case.  This isn't a bug, it's the expected behavior.

Next time this happens, you might want to try seeing if the file is open.  You can use the "lsof" command to show a list of files that are currently open, and grep it for the file you want.

```
lsof | grep /home/some_deleted_file
```

---

### Post by mikerobinson on 2010-03-12
Thanks nemilar. I'll keep that in mind. Marked as solved.

---

