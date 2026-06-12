---
title: "consolidating old backups"
date: 2011-07-24
forum: General Help
---

### Post by samuraix51 on 2011-07-24
I am looking for a way to consolidate my old backups down to just 1

The old backup routine was just to rsync the folder to my backup fileserver. As a result I have a different folder dated for each time I ran the backup.
 - Week_01_Backup
 - Week_02_Backup
   ...

I've got about a years worth of files from backups at about 300G - 400G total, a lot of them are most likely duplicate files

I'm moving to using rsnapshot to run the backups now for easier management and less duplication.

I'm trying to find the easyist way to merge all the old backups down to 1 folder

I'm thinking taking the most recent backup, and rsyncing the ones prior to it. Or would the other way be better? rsyncing everything to the oldest backup.

any other ideas or insights on how to merge them down would be much appreciated

---

### Post by seawolf167 on 2011-07-25
What about just rsyncing the backups individually all to one new folder? If you use the update switch it should only take the most recently modified file(s) each time there is an existing file conflict.

---

### Post by samuraix51 on 2011-07-26
That might be the way to go, just syncing to a new folder entirely. I'll have to try it on a small set of it and see if it works

---

