---
title: "Archive File Attribute using SimpleBackup"
date: 2010-05-01
forum: General Help
---

### Post by TaiChiRabbit on 2010-05-01
I just want to check whether a file has been backed-up using Simple Backup - I do daily incremental backups and a weekly full backup.  However using lsattr in terminal shows a line of '-' prior to the filename, indicating that none of the extended file attributes has been set.  I was under the impression that whenever a file was backed up the archive file attribute would be set, and then if the file was altered the archive attribute would be unset, indicating it needed to be included in the incremental back-up.

Does Simple BackUp change the archive attribute, and how can you check the setting of the archive attribute?

Thanks!

---

