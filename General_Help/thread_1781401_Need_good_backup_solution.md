---
title: "Need good backup solution"
date: 2011-06-13
forum: General Help
---

### Post by Calcipher on 2011-06-13
I have a machine that I need to backup up to an external hard drive.  In the past, I have been using [BackInTime]("http://backintime.le-web.org/"), but I am [having problems with it]("https://bugs.launchpad.net/backintime/+bug/784840") that basically make it unusable and it [seems to no longer be in development]("https://answers.launchpad.net/backintime/+question/158968").  This means I need a new piece of backup software; I must say that I do know that writing my own rsync script is an option, but I don't want to spend the time as my include/exclude list is a bit complicated and I want to automate removals in smart ways.  

Thus, I need to find a new backup solution.  So far, I have tried the following:
[LIST=1]
[*] Duplicity: A good solution, but it will require as much work as an rsync script to properly automate.
[*] Deja-dup: Way too simple.  I can't schedule incremental backups hourly, I can only exclude folders and not specific files, it has almost no auto-remove options.
[*] Luckybackup: I don't know, it just completely fails to work after I've set it up.
[*] Backupninja: Using ninjahelper, there seems to be no options to backup to a local drive.  One can get around this by setting the destination host as local host, but they you have to create an ssh user for the backup process and I'd rather not do that.
[/LIST]

What I need
[LIST]
[*] Ability to specify directories/files to backup.
[*] Ability to exclude specific directories/files.
[*] Ability to override an exclude with an explicit include (e.g. --exclude="/A" --include="/A/b")
[*] Ability to schedule backups 
[*] Ability to skip backups if backup location is not present (it is an external drive after all)
[*] Ability to smartly schedule deletions.  I loved the 'smart remove' option in BackInTime, but I don't need to be that picky.
[/LIST]

Does anyone know of any good backup solutions that are still in development (e.g. TimeVault seems to be dead)?

---

### Post by aeronutt on 2011-06-13
Sounds like grsync and grsync-batch might be the a choice.

---

### Post by sammiev on 2011-06-13
I use [Clonezilla]("http://clonezilla.org/clonezilla-live.php") to backup all my stuff and it will also backup multiple OS even at the same time and can be set to check the backups as well to make sure they are good. Never tried it to do everything you are looking to do but worth the read. GL :)

---

### Post by Calcipher on 2011-06-14
Hrm, my thoughts so far.  grsync is mostly there, it just needs a way to store backups in different folders (based on date?) and auto remove on command.  

Sammiev, could you describe in more depth how you are using CloneZilla to back stuff up.  It was my understanding that it created disk images.

---

### Post by sammiev on 2011-06-14
> **Calcipher said:**
> Hrm, my thoughts so far.  grsync is mostly there, it just needs a way to store backups in different folders (based on date?) and auto remove on command.  

Sammiev, could you describe in more depth how you are using CloneZilla to back stuff up.  It was my understanding that it created disk images.

Since I have a large backup unit I do full image backs of my HD. There are other options as well instead of full image backups, but I haven't tried them. GL :)

---

### Post by demck85 on 2011-06-14
Crashplan works great for onsite and offsite.

---

