---
title: "Sbackup to FTP not working"
date: 2011-09-05
forum: General Help
---

### Post by fetflex on 2011-09-05
Hi

Im trying to make a backup with sbackup to my Windows FTP server. But without much luck.

When i try to run a test it says:
[I]Unable to access remote destination.
Operation failed.[/I]

Then when i look in the log at the FTP end i can see that it has run some tests and it seems that it's trying to delete an folder with an DELE command:
[I]
ubuntu, DELE /sbackup-dir-1315208496.84-7feaa775-efc9-4a94-aaea-fa947c7ee62a.tmp

ubuntu, delete file '/sbackup-dir-1315208496.84-7feaa775-efc9-4a94-aaea-fa947c7ee62a.tmp' -> 'F:\Backup\sbackup-dir-1315208496.84-7feaa775-efc9-4a94-aaea-fa947c7ee62a.tmp' --> Can't delete file.

ubuntu, 450 File "/sbackup-dir-1315208496.84-7feaa775-efc9-4a94-aaea-fa947c7ee62a.tmp" can't be deleted.[/I]

Hope that someone can help.

---

### Post by fetflex on 2011-09-07
Nobody seen this before?

Deos anyone of you do an FTP backup to a Windows machine? If so what server software do you run?

---

