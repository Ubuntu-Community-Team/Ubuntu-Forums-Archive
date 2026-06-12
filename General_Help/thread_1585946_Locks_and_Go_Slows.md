---
title: "Locks and Go Slows"
date: 2010-10-01
forum: General Help
---

### Post by Quarkrad on 2010-10-01
Two questions please - newbie

1.  Updated PC (hasn't been updated for some time) and running on kernel 2.6.32-24.  Wow - this 10.04 pc is now running so slow - like a win machine. How do I revert back to an old kernel - is it as easy as deleting 2.6.32-24 via Synaptic?

2.  All the pictures/jpgs in home/pictures have a lock icon top right hand corner.  I'm not sure what this is/how it got there - but when I run rsync to copy them to another internal HD rsync stops doing anything when it gets to the first jpg.  Could it be something to do with the lock icon?  (I'm copying /home to another HD - all the other folders in /home appear to get copied - just a problem with the pictures folder).

note.  This is not my machine but I did install 10.04 (clean).

---

### Post by andrewthomas on 2010-10-01
> **Quarkrad said:**
> Two questions please - newbie

All the pictures/jpgs in home/pictures have a lock icon top right hand corner.  I'm not sure what this is/how it got there - but when I run rsync to copy them to another internal HD rsync stops doing anything when it gets to the first jpg.  Could it be something to do with the lock icon?  (I'm copying /home to another HD - all the other folders in /home appear to get copied - just a problem with the pictures folder).

note.  This is not my machine but I did install 10.04 (clean).
The permissions on the files seem to have been changed.

---

### Post by ajgreeny on 2010-10-01
Where did the pictures come from?  Was it an existing home folder or partition, and if so was the owner the same as the current owner?

---

### Post by Quarkrad on 2010-10-02
Sorted - thanks.  It was permissions - everything was set to root.  Managed to changed to user by gksudo nautilus and changing permissions.

---

