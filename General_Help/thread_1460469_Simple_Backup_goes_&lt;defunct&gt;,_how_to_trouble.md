---
title: "Simple Backup goes &lt;defunct&gt;, how to troubleshoot?"
date: 2010-04-22
forum: General Help
---

### Post by Rocket J Squirrel on 2010-04-22
I installed Simple Backup Suite ([https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite](https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite)) on this Karmic box last week and it ran fine the first time. Now it locks up shortly after I tell it to run a backup. 

ps shows

```
3273 ?        00:00:01 gksu
 3274 ?        00:00:01 simple-backup-c
 3279 ?        00:00:02 sbackupd <defunct>
 3287 pts/0    00:00:00 ps
```

I re-installed the application, which didn't help. 

Can anyone suggest some troubleshooting tips?

---

### Post by Rocket J Squirrel on 2010-04-27
Bump-o-rama?

---

### Post by FrankyG on 2010-05-14
I got the same problem running sbackup on Lucid.
Any pointers to workaround this?

---

### Post by FrankyG on 2010-05-14
Rocket, you can start it manually from the command line. So, I think that running it as a cron job would work as well.

$ sudo sbackupd

Bug reports have already been filed here:
[https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/550261](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/550261)
(and [https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/558318](https://bugs.launchpad.net/ubuntu/+source/sbackup/+bug/558318), which is a duplicate of the above).

---

### Post by drewster1829 on 2010-05-15
Thanks, I had the same problem in Lucid. I'll run it from the command line now (I had it set to do manual backups before anyway).  

I've always wanted to learn how to use cron, but I've never set up an automated cron job.  Maybe I should take this as an opportunity to learn. :)

---

### Post by FrankyG on 2010-05-16
drewster, good idea to take a look at how cron works. :)

if you set up an automated backup in simple backup's gui under tab "Time", a cron job file will get created, which you can inspect like so:

$ cat /etc/cron.d/sbackup

btw: backups via cron work as expected

---

