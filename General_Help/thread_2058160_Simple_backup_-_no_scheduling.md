---
title: "Simple backup - no scheduling"
date: 2012-09-15
forum: General Help
---

### Post by oygle on 2012-09-15
Have used simple backup up to version 10.04 of Ubuntu, and having recently installed 12.04, I see Simple backup has no schedule, as the TAB for schedule is greyed out.

Any 'fix' for this, as there is no automatted backups, I have to manually run it from sbackup.

The backup that comes with 12.04 (deja-dup) is too basic, it doesn't have provision for exluding paths and/or files.

What are people using for a GUI backup.

Oygle

---

### Post by jerrrys on 2012-09-15
I like grsync and luckybackup

---

### Post by oygle on 2012-09-19
Is luckbackup better than Simple backup ?

I need an app that does full backups, as well as incremental backups.

---

### Post by SlugSlug on 2012-09-19
My preference is backintime :)

---

### Post by oygle on 2012-09-19
Thanks, I have installed backintime, and am running it now. What happens when there are files deleted from the 'source' path ? Does backintime also delete them from the destination backup path, so the snapshot remains true ?

---

### Post by SlugSlug on 2012-09-19
It keeps multiple snapshots that so the file you deleted will be in yesterdays snapshot - just not tomorrows

---

### Post by oygle on 2012-09-19
Okay thanks.

---

