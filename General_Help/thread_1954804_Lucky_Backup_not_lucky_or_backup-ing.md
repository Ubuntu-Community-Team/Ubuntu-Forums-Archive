---
title: "Lucky Backup not lucky or backup-ing"
date: 2012-04-08
forum: General Help
---

### Post by x-shaney-x on 2012-04-08
I am trying to use Lucky Backup to backup photos in my home folder to a FAT32 partition but it is failing to even copy a single file.

the log file is showing a lot of errors like this: ```
rsync: chgrp "path/to/backup/folder" failed: Operation not permitted (1)
```
And this:```
rsync: mkstemp "/path/to/photo/.photo.jpg.ggUc9P" failed: Operation not permitted (1)
```

The odd thing is, I have a kubuntu install and am able to make backups using Lucky Backup to exactly the same directory with no problems at all.

In fact, this is not the first time I have had problems with ubuntu and FAT partitions, I have also had trouble manually copying files to them too.

---

