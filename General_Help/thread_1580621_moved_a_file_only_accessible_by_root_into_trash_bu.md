---
title: "moved a file only accessible by root into trash but cant see it?"
date: 2010-09-23
forum: General Help
---

### Post by fuzzylogic25 on 2010-09-23
I installed simple back up program, i hated it. but it created a backup in /var/backup. so i typed gksudo nautilus to access it since it wouldnt let me open the folder normally. Then, i moved the folder into trash, but i cant see it in the trash?

Where is it? is it possible that it can only be seen in trash if i log on as root?

---

### Post by SteveDee on 2010-09-24
> **fuzzylogic25 said:**
> I installed simple back up program, i hated it. but it created a backup in /var/backup. so i typed gksudo nautilus to access it since it wouldnt let me open the folder normally. Then, i moved the folder into trash, but i cant see it in the trash?

Where is it? is it possible that it can only be seen in trash if i log on as root?

When deleting files in Nautilus as root, they go to roots trash folder:-
/root/.local/share/Trash/files

---

