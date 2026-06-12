---
title: "Rsnapshot wrong behaviour"
date: 2006-03-02
forum: General Help
---

### Post by el3ktro on 2006-03-02
I've been backing up my data files for over a year with rsnapshot now, and it always worked perfectly. I recently upgraded to rsnapshot 1.2 - and suddenly all the backup dirs have the wrong date. Usually, when rsnapshot creates a backup say at 15:00h, then it "touches" the backup dir after the backup is finished so that the backup dir has the timestamp of the time where the backup has run.

Since 1.2, the log files still say that rsnapshot is doing this, but all the snapshot dirs have the wrong date, they don't get touched. When I touch them manually everythings fine.

Has anybody else seen this?


Tom

---

