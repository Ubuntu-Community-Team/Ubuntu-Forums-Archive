---
title: "Archive directory when changes are made"
date: 2010-07-09
forum: General Help
---

### Post by F.McC on 2010-07-09
I'm trying to put together a backup script to use to archive my work daily. Rsync and cron are what i'm using so far for backup, but what i'd like to do is to create a historical archive of my work as I progress as well, but updating it all blindly daily seems wasteful.

So i'd like to do something along the lines of ```
rsync -av ~/PATH/TO/FILE ~/ARCHIVE/BACKUP_`date '+%y_%m_%d'` 
```But only when a file has been changed, so i'd end up with 
```
~/ARCHIVE/BACKUP_10_07_09
~/ARCHIVE/BACKUP_10_07_13
~/ARCHIVE/BACKUP_10_07_19
```rather than,
```
~/ARCHIVE/BACKUP_10_07_09
~/ARCHIVE/BACKUP_10_07_10
~/ARCHIVE/BACKUP_10_07_11
~/ARCHIVE/BACKUP_10_07_12
~/ARCHIVE/BACKUP_10_07_13
~/ARCHIVE/BACKUP_10_07_14
```I have come across tar as well, and using that would be good rather than rsync or cp, but its just determining when to backup thats the problem.

Just a bit new to scripting and i have no idea how to do this.

---

