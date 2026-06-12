---
title: "backing up!"
date: 2010-02-27
forum: General Help
---

### Post by tombutcher1990 on 2010-02-27
hi guys

little help required.

i've got a server 9.10 system, and i've got 2 500GB hard drives installed.

i have the operating system installed on one hard drive, but i want to back everything up to the second one, just incase the drive fails.

now, i found this guide here:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

this looks pretty good. the only thing is, being a server, i want it to back it up systematically (i.e. every week on a thursday evening) and store it on the second drive!

can anyone inform me of exactly how to do this?

i'm not that knowledgeable with linux, but i'm sure there must be a way of scheduling this command to run on a timer. and can anyone possibly edit the code for backing up so that it backs up to my second hard drive rather than the root of the filesystem??

---

### Post by Apollo87 on 2010-02-27
Check out cron for scheduling commands:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Then just make a bash script of those commands in that backup tutorial. You'll have to change the filepath in the tar command to be in your second hard drive. Don't forget to change the exclude for the backup file too.

ex:
```
tar cvpzf /media/second.hard.drive/backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/media/second.hard.drive/backup.tgz --exclude=/mnt --exclude=/sys /
```

---

