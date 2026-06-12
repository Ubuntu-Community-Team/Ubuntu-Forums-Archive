---
title: "Freeware Backup recommendations"
date: 2012-09-17
forum: General Help
---

### Post by kakashi_12 on 2012-09-17
I want a backup application that backs up single files and folders (not the system). I already have an app for that and I like to keep the system and files separately (like an image and file backups).
 
I would prefer it work with both Windows 7 and Linux.
 
I have already tried Nero BackItUp, Windows 7 built in backup, and Western Digital Sync Backup. But they all give errors.
 
What do you recommend that will work. I thought of Carbonite, but I already have an external drive. So I shouldn't really be paying a yearly fee.

---

### Post by kakashi_12 on 2012-09-17
_

---

### Post by dcstar on 2012-09-18
> **kakashi_12 said:**
> I want a backup application that backs up single files and folders (not the system). I already have an app for that and I like to keep the system and files separately (like an image and file backups).
 
I would prefer it work with both Windows 7 and Linux.
 
I have already tried Nero BackItUp, Windows 7 built in backup, and Western Digital Sync Backup. But they all give errors.
 
What do you recommend that will work. I thought of Carbonite, but I already have an external drive. So I shouldn't really be paying a yearly fee.

Unison

---

### Post by markbl on 2012-09-18
I've been very happy using [rsnapshot](http://rsnapshot.org/) for many years running on my linux machine and backing up that machine plus my wife's windows pc. I install the free deltacopy (rsync server for windows) on her machine so rsnapshot can pull the files.

---

### Post by kurt18947 on 2012-09-18
Luckybackup, a front end for rsync found in the repositories seems pretty good for backing up or syncing folders.  I used grsync  - also found in the repositories - but I didn't find a sync function in grsync despite its name.  It seemed to copy the latest verson of a file or folder from machine A to machine B but not viceversa. There may have been a sync function but it was pretty well hidden.  Luckybackup has a box where I can select either backup or synchronize.

There is also a pure java backup app called DirSync Pro which I tried briefly.  It seemed to work okay and is cross platform.
[http://www.dirsyncpro.org/](http://www.dirsyncpro.org/)

---

### Post by kakashi_12 on 2012-09-18
Thanks for all the recommendations. I'm going to test each one of them.
Also, I need to add that I do not want to really do a full backup every time. I just want to backup the changes (new files, changed files, deleted files, and moved files or folderse).
 
I have been doing research of the difference between DIFFERENTIAL and INCREMENTAL backups. They sounds similar, but I think the one I want is differential.

---

### Post by sandyd on 2012-09-18
> **kakashi_12 said:**
> Thanks for all the recommendations. I'm going to test each one of them.
Also, I need to add that I do not want to really do a full backup every time. I just want to backup the changes (new files, changed files, deleted files, and moved files or folderse).
 
I have been doing research of the difference between DIFFERENTIAL and INCREMENTAL backups. They sounds similar, but I think the one I want is differential.
rdiff-backup.

---

### Post by Rokel on 2012-09-19
duplicati.org

Open source, nice graphical (also windows) client, makes you setup backup schedules and can only backup delta's to harddisk, FTP, SSH, Webdav, Google Drive, SkyDrive,  Amazon and many more.

Client side encryption, incrementals (so you can pick any day of the year to restore and don't overwrite healthy backups with corrupted files)

[http://code.google.com/p/duplicati/wiki/TableOfContents](http://code.google.com/p/duplicati/wiki/TableOfContents)

---

### Post by Rokel on 2012-09-19
> **kakashi_12 said:**
> 
I have been doing research of the difference between DIFFERENTIAL and INCREMENTAL backups. They sounds similar, but I think the one I want is differential.

Make sure you learn a bit about making proper backups, there are some situation where you really wished you did ;) 

Incremental: Full backup on monday, very small incrementals on the others (comparing with the previous day). But you need to restore six backups if you want something back from last saturday.

Differentials: Full backup on monday, bigger difference backup for the following day (comparing with monday) You only need to restore two backups for any other day then monday.


Nowadays with the smart clients that sort everything for you probably want incrementals. Especially for private collections like music, photo's etc.

If you are making huge video productions you could imagine you don't want to restore a temporary 800 GB folder you only used on wednesday to get a 1 GB file you need restored from friday.

---

### Post by kakashi_12 on 2012-09-19
I really don't want to 'run a restore'. I just want to pull my files one by one from my backup hdd.

---

### Post by markbl on 2012-09-19
> **kakashi_12 said:**
> I really don't want to 'run a restore'. I just want to pull my files one by one from my backup hdd.
Did you look at [rsnapshot](http://rsnapshot.org/) as I suggested? It doesn't need any of that rhubarb. It only updates files that change (using rsync's --link-dest option) but to the end user you see a complete tree of dirs/files in each of your daily backups. It only uses disk space for the files + changes, not for the muliple "copies" of complete backups you see as a user. It's great.

---

### Post by kakashi_12 on 2012-09-19
I was looking at it, but I don't see the download version for Windows. That's where majority of my files are. Linux is secondary with less files.

---

### Post by markbl on 2012-09-19
> **kakashi_12 said:**
> I was looking at it, but I don't see the download version for Windows. That's where majority of my files are. Linux is secondary with less files.
You are posting on the ubuntu forums site. I assume you are looking for linux software!?

Anyhow, I also suggested in my first post how rsnapshot can pull files from windows PCs. I suggested you install deltacopy on each windows client pc. That is a windows rsync server. Very easy to install and configure and works well (as I also said, I use it to back up my wife's windows pc). Make the backup area available from the linux server to windows pcs via samba so users can recover their own files from the backup area.

---

### Post by kakashi_12 on 2012-09-19
So do I need to install it on my Windows and Linux partitions both? I have both OS's on the same pc. I don't need to run a server through network app.

---

### Post by stephan0h on 2012-09-19
Hi,
I do it with rsync. Years ago I found a nice script for doing a generational backup with rsync, modified it a bit, and this keeps me going. I have a backup-disk, and from time to time everything is copied there. When I loose something, I manually copy it back (and as it's generational, I have a chance of finding things way back ;-)
cheers,
stephan

---

### Post by kakashi_12 on 2012-09-19
I found an app that works pretty decently. FreeByte Backup. Only disadvantage I'm seeing is that it does not remove/exlude deleted files.

---

