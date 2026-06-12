---
title: "Corrupted files"
date: 2009-09-04
forum: General Help
---

### Post by Zer0Nin3r on 2009-09-04
I was attempting to restore some files I had on backup using Simple Backup.  I'm running into the problem where the process somehow gets interrupted when I locked the computer.

Anyway, the transfer failed per-say.  When looking at my free space, it shows that the space is being used.

My question is: Where are the temporary files stored?  I know that Simple Backup runs as root, so do I need to sudo into Nautilus?

I would like to locate the files and delete them so I can free up the space.  Or is the drive now corrupted and I need to re-install?

---

### Post by realzippy on 2009-09-04
> **Zer0Nin3r said:**
> I was attempting to restore some files I had on backup using Simple Backup.  I'm running into the problem where the process somehow gets interrupted when I locked the computer.

Anyway, the transfer failed per-say.  When looking at my free space, it shows that the space is being used.

My question is: Where are the temporary files stored?  I know that Simple Backup runs as root, so do I need to sudo into Nautilus?

I would like to locate the files and delete them so I can free up the space.  Or is the drive now corrupted and I need to re-install?


shure you read this:
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

As your backup is in /root directory,you can indeed achieve the data
by **gksudo nautilus**;never start nautilus (or other graphical applications) with sudo,use: gksudo

---

### Post by Zer0Nin3r on 2009-09-04
> **realzippy said:**
> shure you read this:
[https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)

As your backup is in /root directory,you can indeed achieve the data
by **gksudo nautilus**;never start nautilus (or other graphical applications) with sudo,use: gksudo

One quick question.  Why use gksudo instead of sudo?  This is the first time I'm hearing about this.  I do not know the differences and haven't experienced any problems in the past running nautilus from sudo.  Maybe I'm just lucky.

Anyway, I was able to solve my problem.  It had to do with the permissions.  All the files where where they needed to be...sort of.  They were viewable under root, but when I tried to view them from my user, they were still in a temporary directory within the directory I was restoring to (if that makes sense), but were inaccessible to me because I lacked the proper permissions.

Anyway, thanks to those for the help.

---

### Post by realzippy on 2009-09-04
Have look,e.g.,here:

[http://ubuntuforums.org/archive/index.php/t-1213216.html](http://ubuntuforums.org/archive/index.php/t-1213216.html)

---

