---
title: "any efficient backup solution for large external HDD?"
date: 2009-10-01
forum: General Help
---

### Post by yanvolking on 2009-10-01
Hello Community,

I have big problem when it comes to backing up my external Hard Disk Drive.  It's a 500 GB unit.  On it I store all my personal files which include over 100 GB of avi format movies, over 100 GB of mp3 music files, Pdf files (scans of official documents etc) GIF files (my photos), office files, databeses etc etc etc . Total size : 350 GB.

In windows it is very easy using the windows backup function.  This allows choosing the whole HDD, deciding on the type of backup (full or incremental) choose destination (other external HDD) and then hit OK. This then generates a progress window which tells me how much has been done, how much remains to be done and the estimated time to completion.  For the 350 GB this usually takes about 5-6 hours on a full backup (from scratch).  As I add a film here, a song there as well as a few other files in all totalling a few MB every month, I then use the incremental option once a month so that the backup file is updated in just a few minutes.

I have tried various UBUNTU backup functions but the experience has been very frustrating:

1) HUbackup simple does not work (nothing happens when I press go
2) File backup manager does not copy anything anywhere
3) Grsync aborts quickly when it falls on files that cause it problems (unreadable or some other minor problem) Windows back-up over passes such problem files.  It just keeps on going with the next and makes a note of the problem file in the final report).

4) Simple Backup backup config did seem to work at first but very slow : about 1GB takes about 30 minutes (175 hours for the 350 GB at that rate!!)  I left it to run that way but during the night something happened because when I came down in the morning the destination drive icon had disappeared from the screen and I had to restart the computer to access it again.  On it was only  47GB of information and the Simple Backup restore fucntion could not detect any restorable data in the backup destination drive.  

Seems simple backup cant handle an archive of 350GB


I like the general options of Simple Backup but I find it too slow, too invisible (no progress dialog box) and if it just hung barely a quater of the way through the process, it's probably not adapted to large multimedia drive backups.

If I could find a suitable backup solution in UBUNTU I would then be able to do without Windows 100% which is my goal.

Any simple command lines such as ...
                   $ sudo (full/incremental)/backup media/disk-1/myfiles    media/disk-2/myfilesbackup????

Or does ubuntu have a clone of Windows Backup?

I am desperate....](*,). please help

Thanks in advance

---

### Post by akakingess on 2009-10-01
I have heard almost everyone rave about Rsync, and I believe there is a gui version of Grsync, but from what I hear it should do everything you want and then you can even schedule it through a quick script and creating a cron job for it.

Edit: Please note, I have not used it personally, just going off of several other posts that I have read, and it seems almost unanimous...

---

### Post by scouser73 on 2009-10-01
You can use [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html") for backing up, it has a GUI that is very easy to use.

---

### Post by AndyCee on 2009-10-01
I'm personally a fan of rsync - I've not heard anything good about grsync for some reason:confused:

An incremental backup is simply:

```
rsync -av  /media/disk-1/myfiles /media/disk-2/myfilesbackup
```

I don't personally do full backups, but all you'd need to do is change the target folder.

If you want a gui you could try "[Back in time]("http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html")". I've only read about it.

I'm sure if none of these suit you, someone will suggest a winner.

---

### Post by StuartN on 2009-10-01
> **yanvolking said:**
> 3) Grsync aborts quickly when it falls on files that cause it problems (unreadable or some other minor problem) Windows back-up over passes such problem files.

This should not happen. Perhaps you could post the rsync command and errors that appear in the Grsync window when running or simulating the command.

---

