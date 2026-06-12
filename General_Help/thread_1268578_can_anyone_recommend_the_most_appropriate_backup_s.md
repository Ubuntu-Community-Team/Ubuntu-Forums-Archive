---
title: "can anyone recommend the most appropriate backup system for me?"
date: 2009-09-17
forum: General Help
---

### Post by yanvolking on 2009-09-17
Hello Community
 
I would like to choose a BACKUP system but am not sure which is best suited to my needs.
 
I store large amounts data (about 10% openoffice type files, 10% photos, and 80% music (mp3) and video (avi) files.  total size to date : 350 GB.
 
When I used windows in a previous life, the backup function suited me well.  The first backup (option : "complete") on a new backup media (removable HDD) took about 8 hours.  But then I would use the "incremental" option which just added the files not backed up since the last backup to the main backup document.  That way I could avoid having to backup the whole thing every time I added a new file of just a few megabytes.  I have recently installed Home User Backup but am no sure if it permits such "incremental backups".  I am a novice and want something quick and simple which works from the GUI environment.  I certainly do not want to have to work with command lines at Terminal Level (for risk of accidentally formating my HD ](*,)).
 
Thanks

---

### Post by keta on 2009-09-17
I have not tried it, but [rsync]("http://www.samba.org/rsync/") seems like a good option for backups. It is command-line, though.

For a GUI, try [Synkron]("http://synkron.sourceforge.net/"). I have used it and works fairly well for what I've done.

---

### Post by tea for one on 2009-09-17
Good morning

Have a look at Grsync - it is available via Synaptic.

---

### Post by scouser73 on 2009-09-17
For backing up I use [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), the tutorial shows you how to use it and in my opinion I think it's an excellent program for backing up data.

---

### Post by ubongo2008 on 2009-09-17
i use clonezilla livecd its free it works and it is fast too

---

### Post by XCan on 2009-09-17
I vote for rsync. ```
 rsync -a /src/path /dest/path 
``` and it's done. :)

---

### Post by Zill on 2009-09-17
I use Simple Backup (sbackup).  It does full and incremental backups, either on demand or on a scheduled basis.

It should already be installed on your system.
Menu: System, Administration, Simple Backup Config (Restore)
[URL="https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite"]
https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite[/URL]

---

### Post by StuartN on 2009-09-17
Another vote for rsync, or the GUI grsync (which is also a handy way to look at and test rsync options). rsync not only transfers the minimum number of files necessary to update the backup, but reduces the number of bytes transferred by some magic algorithm. I have a shell script with lines like this on my Desktop:

```
echo "BACKING UP Desktop" >> backup.log
rsync -avh --delete ~/Desktop/ rsync://Stuart@192.168.1.111:/Stuart/Desktop/ >> backup.log
```

- backup to my account on a remote NAS, (a)rchive mode, (v)erbose, (h)uman readable, --delete files on NAS that no longer exist on Desktop. It is extremely quick after the first time.

---

