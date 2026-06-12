---
title: "Best backup app?"
date: 2012-04-25
forum: General Help
---

### Post by Bucky Ball on 2012-04-25
Hi all,

This has probably been asked a zillion times but what do people use to backup?

I am looking for an app that can backup important files to an external hard drive then compare on the next backup and only backup files that have either changed or are new. 

I have looked at a few; Unison, rsync and a couple of others. Am after something with a friendly GUI (not terminal based) that's reliable and stable. 

All suggestions and comments welcome ... ;)

---

### Post by Bucky Ball on 2012-04-26
Well, I used Simple Backup and backed-up a few directories to the external hard drive. All good but not incremental (as in it doesn't compare what's being backed-up with the existing backup). ;(

Not many options.

I tried Unison to sync a directory on the computer - one I'd like to sync at the end of each day - with one on the external hard drive. It worked, to a point. Synced some files to the empty folder on the external drive but spat a bunch of errors regarding over 50% of them. Odd.

---

### Post by zombifier25 on 2012-04-26
rsync is on of the best option available and many people here will agree :) 'sides, it's built it.
It copies files to another folder, with the option of copying only files that are modified or new and/or deleting files on the destination that are no longer on the source.
I think a GUI for rsync is available, but I don't know any.

---

### Post by surfer on 2012-04-26
i like [back in time]("http://backintime.le-web.org/"). uses rsync behind the scenes.

---

### Post by zeljkojagust on 2012-04-26
@zombifier25 I'm the first one that agrees. Rsync rules for "incremental backups and restores", and it does excellent job!

---

### Post by HermanAB on 2012-04-26
rsync

Read the man page.

It is so simple to use that any GUI based backup program makes it more difficult.

---

### Post by surfer on 2012-04-26
> **HermanAB said:**
> rsync

Read the man page.

It is so simple to use that any GUI based backup program makes it more difficult.

even i agree to that.

---

### Post by schru on 2012-04-26
i suggest trying grsync, its a gui for rsync, and it works just fine for me

---

### Post by Bucky Ball on 2012-04-26
> **schru said:**
> i suggest trying grsync, its a gui for rsync, and it works just fine for me

Yea, works okay for me, too. On one directory. On another I get 'Completed with Errors' even though the dry-run is error-free. 

Back in time seems to work well. It achieved what I wanted without any problem; backed up three important directories to the external hard drive.

---

### Post by Zill on 2012-04-26
> **Bucky Ball said:**
> Well, I used Simple Backup and backed-up a few directories to the external hard drive. All good but not incremental (as in it doesn't compare what's being backed-up with the existing backup)...
Simple Backup (SBackup) *does* do incremental backups:
> Sbackup does NOT create a new backup file each time it runs. Instead, it creates an incremental backup, that is to say only new files modified since the last backup (full or incremental) are archived.
[BackupYourSystemSimpleBackupSuite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")

I have used this app for years to do a full backup once a week and an incremental backup every day.  This can be easily set up via the GUI.

---

