---
title: "Backup application"
date: 2010-06-01
forum: General Help
---

### Post by Toube on 2010-06-01
Hi,

does anyone have any good suggestions for a good backup application in ubuntu? For the os itself I'm already backuping it up using .tar compression.

Is there any program for Ubuntu like Winscp for windows? With Winscp you can run backups / synchronize directories of your choice.

Regards,

Toby

---

### Post by Tamlynmac on 2010-06-01
I use [Sbackup]("http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html") and have had zero problems recovering data including system files.

Extremely selective backups are easy to setup and custom time settings simplify scheduled backups.

Good Luck.

---

### Post by aysiu on 2010-06-01
I'd recommend rsync, which will copy only files that have been added or changed since the last backup.

```
rsync -av /path/to/source-of-backup /path/to/target-of-backup
``` There is also a graphical user interface for it called Grsync.

---

### Post by sarin_cv on 2010-06-01
'backin time' ... don't know whether it compresses....

---

### Post by Zerocool Djx on 2010-06-01
Aptone works well for storing packages, but not like files of your work

---

### Post by Toube on 2010-06-01
thanks for your suggestions, I will look in to these and see which of these are going to suit my backup needs best :)

---

### Post by inameiname on 2010-06-01
I guess I'll throw in Remastersys. Not exactly the same sort of backup program as the others mentioned here, but it's my preferrred. Quite easy to make a full system backup of everything, with the addition to run off a cd/dvd as a Live disc if you wish too. Just another option. However, as you use of tar compression already, as well as for what you want, rsync or sbackup are good choices.

---

