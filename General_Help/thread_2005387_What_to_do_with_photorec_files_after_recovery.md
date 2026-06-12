---
title: "What to do with photorec files after recovery?"
date: 2012-06-17
forum: General Help
---

### Post by oneguy on 2012-06-17
After a little fiasco with repartitioning, I used photorec to recover files from a previous Ubuntu install. The recup_dir folders (1747 count) are now taking up a huge amount of space, and what's more, they are all locked and inaccessible. I can't open them or move them. My questions are:

1. How do I unlock the directories? (Graphical interface preferred because I'm not good at terminal, though I'll gladly use the terminal if you recommend it.)

2. How do I figure out what data is what once they're unlocked? I'm really only looking for a handful of particular files.

3. Any other advice?

I appreciate anyone willing to take the time.

---

### Post by oneguy on 2012-06-17
Okay, so I've managed to unlock the folders, which were located in my Downloads folder, by entering this terminal command from my home folder:
```
sudo chown -R ben:ben Downloads

```
It worked, unlocking all of the files. Now, I need to sift through them and find the data I need, then dispose of the rest--so questions 2 and 3 still stand. Thanks.

---

