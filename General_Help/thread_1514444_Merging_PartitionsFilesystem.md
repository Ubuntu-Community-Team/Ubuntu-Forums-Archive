---
title: "Merging Partitions/Filesystem"
date: 2010-06-21
forum: General Help
---

### Post by carlexpc on 2010-06-21
Hi everyone!

Is it possible to merge two or more partitions/filesystem, say, ext4 into one single partition?

TIA.

---

### Post by arrange on 2010-06-21
You mean - without losing data on them?

---

### Post by cheezburger on 2010-06-21
Technically, it is possible but I recommend backing up anything of importance first, as sometimes you can lose data.
I've always found that [GParted]("http://gparted.sourceforge.net") is good and have never lost data with it before, however, better safe than sorry!

---

### Post by carlexpc on 2010-06-21
> **arrange said:**
> You mean - without losing data on them?

Yes, that's what I would like to do. I restored an image from a 160GB drive to a 320GB drive using clonezilla. The process did not automatically adjusted the filesystem size proportionally to the target drive.

I would like to merge the remaining 160GB free space (unformatted/unmounted) to the adjacent partition (i.e. /home) without losing the data on /home.

---

### Post by arrange on 2010-06-21
> **cheezburger said:**
> Technically, it is possible but I recommend backing up anything of importance first, as sometimes you can lose data.
I've always found that [GParted]("http://gparted.sourceforge.net") is good and have never lost data with it before, however, better safe than sorry!
You've merged partitions in GParted without losing data? How did you do it?

---

### Post by arrange on 2010-06-21
> **carlexpc said:**
> Yes, that's what I would like to do. I restored an image from a 160GB drive to a 320GB drive using clonezilla. The process did not automatically adjusted the filesystem size proportionally to the target drive.

I would like to merge the remaining 160GB free space (unformatted/unmounted) to the adjacent partition (i.e. /home) without losing the data on /home.
Aha, this is not merging IMO but resizing (just expand the */home* partition over the free space), should be no problem for GParted, but, as *cheezburger* says, backup anyway!

---

### Post by carlexpc on 2010-06-21
> **arrange said:**
> Aha, this is not merging IMO but resizing (just expand the */home* partition over the free space), should be no problem for GParted, but, as *cheezburger* says, backup anyway!


I've done it using gparted. I booted a LiveCD then resized until the remaining free space is used.

---

