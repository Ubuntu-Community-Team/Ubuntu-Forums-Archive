---
title: "Backups... the never ending debate"
date: 2010-04-23
forum: General Help
---

### Post by abean on 2010-04-23
Hi All,

I have been reading up on various ways to implement backups. From rsync to Bacula via acera....

I was wondering whether the wise among us could suggest an ideal solution for this situation:

I have one rather large dir which needs backing up. About 23 gigs.

A weekly backup will be taken off site some way, either uploading to an ftp server or on a usb drive taken off site. I'd rather a remote server as then I don't have to look at it or anything once its setup to run.

I'm half thinking of just tar ing the folder, zipping/encrypting it and sticking it on a usb drive. Is there a problem doing it this way? I have heard rsync is very good but the different between a full backup and incremental confuses me... Can i increment daily and take a full backup weekly? Does this have to be a seperate command?

Cheers

Abe

---

### Post by ajgreeny on 2010-04-23
You can certainly use rsync with cron and different options chosen for the daily incremental and weekly full backups with no difficulty at all, though I have to admit that I have never used rsync for anything other than an incremental backup.

You will perhaps also need to consider if you need to keep the previous full backup when you do the next weekly one, or if it can be deleted then another remade as a new full one.

The default option for rsync is, I think, to do incremental backups, but by using cron to set the options to the command there is no problem, and the simplest way is probably to use shell scripts, one for the daily and another for the weekly, with the rsync options changed in the command in the shell script.

---

### Post by abean on 2010-04-23
That makes sense.

I guess there are two purposes for the backup.
1) Historical Record
2) Data Recovery

I guess I can set up to rsyncs.
1) Daily Incremental backup to remote site
2) Weekly full backup to remote site

Does that make sense?

---

### Post by psusi on 2010-04-23
Tar will do daily incremental backups, but when it finds a file has changed it puts the WHOLE file in the daily backup.  There is rdiff backup that finds only the parts of the files that have changed and puts them in the incremental backup.

rsync is not a backup tool; it is a copy tool.  You can use it to make a full copy of your files on an off site server, then keep updating it every day and rsync will only transmit the parts of the files that have changed.  This keeps a full uncompressed copy of your data though, rather than storing it in an archive file that can be compressed.

---

### Post by abean on 2010-04-23
Any other ideas? Does ubuntu have a default supported backup solution?

---

### Post by john newbuntu on 2010-04-23
Just a general note: Always have a mechanism of knowing whether your backups succeeded.  For example, if you are using batch scripts, check exit values after running rsync or tar.  Have a way of getting an e-mail when something fails.  Sometimes after a prolonged period of time, backups fail and it goes undetected.

---

### Post by Untitled_No4 on 2010-04-23
Have a look at Time Drive. It's in the Ubuntu's PPA. 
[http://www.oak-tree.us/blog/index.php/science-and-technology/time-drive](http://www.oak-tree.us/blog/index.php/science-and-technology/time-drive)

---

