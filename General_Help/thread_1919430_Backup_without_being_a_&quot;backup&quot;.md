---
title: "Backup without being a &quot;backup&quot;"
date: 2012-02-02
forum: General Help
---

### Post by Despotism on 2012-02-02
I have spent the last few hours looking at different methods, different options, different approaches.. Unfortunately the "subject matter" is just too board to really refine down enough to what I'm actually looking for. I have a 6TB RAID5 Array. The important files are backed up on a remote 6TB RAID5 Array (This is setup with Ubuntu's backup ability). I'm running Ubuntu 11.10. And XMBC as a media center.

I am looking for a way to have a "quick" recovery option that doesn't involve hours of scanning.. Because of the sheer size of the media array (3.5TB) I do not want a "Shadow" copy setup or a "Snapshot" of the files, because it would consume a lot of space on files which I do not care if I lose (video files).

What I do want is if I delete or edit any one of the files it takes the old file/delete keeps it for about time before auto-deleting itself. I would like to do this at what appears to be the file-system level, So I whoops delete a file it's backed up.
Kinda of like a Trashcan, but it does it for Modified files as well. So if I create a file, save it, edit it, and save it again it does something like a shadow-copy where it keeps the "old" version of the file..

Is this possible?

You may ask why would I want an undelete with the remote 6TB array, I could just recover. The backup that pushes files to the remove happens once a month. So I need an "undelete" for anything added to the array in that month, and deleted before it gets to the remote storage.

---

### Post by lisati on 2012-02-02
*Thread moved to **General Help**.*

---

### Post by i.r.id10t on 2012-02-02
How remote?  If just another box on your LAN I recently read an article about doing software RAID over network...  

[http://www.linuxjournal.com/article/8149](http://www.linuxjournal.com/article/8149)

---

### Post by Despotism on 2012-02-03
> **i.r.id10t said:**
> How remote?  If just another box on your LAN I recently read an article about doing software RAID over network...  

[http://www.linuxjournal.com/article/8149](http://www.linuxjournal.com/article/8149)

It is actually using Hamachi.. It's not my box it's a friends, and we use each other as a remote storage device to save those important files we simply can't lose. Pictures, Movies of Kids, important documents, events etc. Total Offsite data is something like 4GB each. It's not perfect, but we both had harddrive failures years ago and both lost files, we both vouched that would never happen again. Two RAID5 Arrays housing those "can't lose files" both in remote locations from each other adds to the integrity of data retention.

The rest of the stuff is just media files and some general stuff nothing special. Loss of that data is not important as we can just get the file again. Hamachi is OK for a smaller amount of data is not a problem, but using each other as backup for everything we do is not desired, and really it would be slow.

----

It is actually the non-backed up data I'm focused on. I recently deleted part of my daughter's youtube video downloads (music she likes etc) I had to redownload them but I inevitably missed a couple of songs, ones she asked what happened.

This brings me to the small question on "Temporary recovery space" A place where files go when they are to be overwritten or deleted, kept there for a while and then auto-deleted or I can just go in and clean them out. I looked at Undelete, however the rather massive array makes file recovery take a stupidly long time.

There are "Trashcan/Recycle Bin" options but they do not work for Edited files, things like Shadow copy/Snapshot are OK, but I'm maybe looking for more of a "Historical Archive" function.

And it does this automatically at the filesystem level, so even If I do #sudo rm * it moves all the files to "Historical Archive/Trashcan/Recycle Bin"

If Deleted go here + rename with filename + time index.
If Edited copy original here + rename with filename + time index.

---

### Post by kvsm on 2012-02-03
Maybe a bit of a straightforward blanket approach, but it sounds like dumping the whole lot into a version control system might provide some of the protection you're after?

---

### Post by TheFu on 2012-02-03
There are lots of different backup methods.  Based on what you are decribing, I think the best for you is either 
* Back in Time
or
* rdiff-backup

**Back-in-Time** has a gui and is meant for end-user backups. You can set up snapshots that happen every 5 minutes, every hour, every {insert-time-period}.  Over time as the snapshots get older, they are removed.  The important things about Back-in-Time
* Your target file system needs to support hardlinks (ext2/3/4, jfs, xfs, btrfs, etc work, NTFS does not)
* The target file system (partition) needs to be different from the source, but still be local to the machine.  NFS may work, but I know that sshfs does not.
* Nothing is compressed, so even when you only have weekly snapshots, if files are constantly changing, this will grow.
Besides those items, it is extremely easy to use.  Space management is built-into the program.

**rdiff-backup** is used much like rsync would be used, but it behaves more like a reverse incremental backup. The last backup is a mirror of the source files. Every old "version" is a diff of the changes over time.  Most of your files don't change too often, so this is very efficient.  Older versions of files are stored as compressed differences. It is pretty efficient.  I keep 30/60/90 days of backups for most of my systems here. My script automatically removes any backup over 630/0/90 days old.  For my HOME, it uses about 10% more storage than the mirror takes for 60 days. 
I do not backup videos with this.

Both of these tools are in the distro repository.
Both these tools store files in a directory structure that is easy to understand and a copy is how you restore a single file. Simple.

---

### Post by Despotism on 2012-02-03
Thank you kvsm and TheFu for your answers.

I'm using rdiff to back-up the vital files already. It does exactly what I need it to do there, but is not quiet what I am looking for over all. I'm beginning to think a function I am looking for doesn't exist.

Bazaa is very interesting and I've installed that on a test box to see how it works. There is a learning curve I need to overcome first :) but I believe it may do what I need it to do.

The main focus was not having a copy of the file until it's actually deleted, changed, edited, etc. The data is somewhat secure on the RAID5 array, important files are backed up in a remote location. All I really need is if for some reason something changes on any of these files, take a copy of the old file before the changes are made and store it.

It seems like a simple task, but one that doesn't appear to be automatic anywhere. The best description I've come across is a FileSystem level Trash Can/Recycle Bin.. FileSystem detects a change to a file is about to take place, it locks the file, takes a backup, open it up for change.

Clearly some things like "Moving" to a new location or "Renaming" it doesn't back it up.. I guess what I'm looking for is an "Undo" with certain amounts of history and file retention.

Thank you again for your suggestions if BaZaa does what it appears to do, this may be the closest thing to an UNDO I've seen. I'm not going to use Back-In-Time because it basically does a copy to a different location in a way rdiff is superior because it will not backup files again which have no changed.

That is kind of why I want to try to get BaZaa working, that is one of it's claims.

Thank you again to the both of you.

---

### Post by TheFu on 2012-02-03
Oh.  Perhaps you need a ZFS pool or LVM2 and want to take snapshots constantly - perhaps every 15 minutes and automate how many you keep around to manage the disk space.

BTW, rdiff and rdiff-backup ARE different, but your assessment is still valid.

---

