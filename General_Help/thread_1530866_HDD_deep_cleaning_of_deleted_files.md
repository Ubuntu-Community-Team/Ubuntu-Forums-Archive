---
title: "HDD deep cleaning of deleted files"
date: 2010-07-14
forum: General Help
---

### Post by Yappix on 2010-07-14
Hi,

Is there a way to deep clean the supposedly "empty" areas of HDD. I've found "shred" and similar tools by googling, but they allow either deleting a file or complete wipeout of a HDD. What I'd like to do is clean up what's left of already deleted files (which can probably be still "undeleted") on a live HDD (with useful data, which doesn't need to be destroyed).

Thanks in advance.

---

### Post by wojox on 2010-07-14
Check out Bleachbit. It's in the repo's. There's also secure-delete but it doesn't work well for ext3/4

---

### Post by Yappix on 2010-07-14
Awesome! Thanks, wojox, bleachbit does have the needed option!

---

### Post by wojox on 2010-07-14
Your Welcome. ;)

---

### Post by belkinsa on 2010-07-14
Don't forget to mark is "SOLVED"

---

### Post by Seeked on 2010-07-14
You may want to consider using: sfill /path/to/mount/point

I believe it is more thorough than bleachbit.

---

