---
title: "Simple backup to an external harddrive"
date: 2010-06-26
forum: General Help
---

### Post by Ron W on 2010-06-26
Hello

I'm wanting to use Simple Backup to save the backup files to an external harddrive. I'm not having much success even when I press the 'Backup now' button. However, I am able to backup onto the internal harddrive. Can anyone give me any advice on how to get Simple Backup to save files to the external harddrive, please?

Thanks

Ron

---

### Post by bobcollard on 2010-06-26
> **Ron W said:**
> Hello

I'm wanting to use Simple Backup to save the backup files to an external harddrive. I'm not having much success even when I press the 'Backup now' button. However, I am able to backup onto the internal harddrive. Can anyone give me any advice on how to get Simple Backup to save files to the external harddrive, please?

Thanks

Ron
Start it in Terminal:
```
sudo sbackupd
```

---

### Post by Rubi1200 on 2010-06-26
Hopefully this might answer your question:

[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

See the section entitled Destination Tab

---

### Post by bobcollard on 2010-06-26
The problem isn't the program or how he is using it, it's a known bug in 10.04.
```
sudo sbackupd
```
is a workaround.

---

### Post by Ron W on 2010-06-29
Thanks Bob.

I've just done as you've suggested and it is now working.

Much appreciated

Ron

---

### Post by bobcollard on 2010-06-29
> **Ron W said:**
> Thanks Bob.

I've just done as you've suggested and it is now working.

Much appreciated

Ron
You're welcome.  Someday they might get this fixed right.  Watch your upgrades.

---

