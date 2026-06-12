---
title: "rsync - how to MOVE, not COPY?"
date: 2010-03-17
forum: General Help
---

### Post by Lockheed on 2010-03-17
This is what I got to so far:
```
rsync -axvS --remove-source-files
```
however, there are two problems with it - one disqualifying and one annoying:

1. it deletes source files AFTER all files are transferred. This is useless, as I have not enough disk space for it. I need source files to be deleted as soon as they are copied.
2. it leaves empty directories behind

How can I remedy at least the first problem?

EDIT:
Scratch that. It actually does remove source files while copying after given folder has been completed.

---

### Post by blueridgedog on 2010-03-17
I assume you have determined that the mv command will not work?  Your comment about space implies that it may be files being moved on the same file system, which make make mv work for you.

---

### Post by Lockheed on 2010-03-18
mv does not preserve timestamps and this is crucial.

---

### Post by blueridgedog on 2010-03-18
Then my only idea would be to write a bash script that uses rsync and removes the directories.

---

### Post by Copperblade on 2011-12-23
I know this thread is old, but I was looking for an answer to this.  The best thing to do is to use cp -pl which will add hard links instead of actually copying (preserving your disk space) and then remove the original tree.

---

### Post by oldos2er on 2011-12-23
Closed, necromancy.

---

