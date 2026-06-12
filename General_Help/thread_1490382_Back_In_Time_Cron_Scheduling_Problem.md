---
title: "Back In Time Cron Scheduling Problem"
date: 2010-05-22
forum: General Help
---

### Post by wadam on 2010-05-22
For a while now, I've been using Back In Time to create backups of my home directory on an external drive.  I've recently noticed that it has stopped backing up automatically.  Today, I did some checking, and I discovered that Back In Time seems unable to create the cron job it needs to be able to run automatically.  I ran backintime-gnome from the terminal, and here is the error output I came up with:

```
Snapshots path: /media/Backup HD
Automatic backup: Every Hour
/var/spool/cron/crontabs/**my username**: Permission denied
crontab: error renaming crontabs/tmp.DKOFfv to crontabs/**my username**
rename: Operation not permitted
/var/spool/cron/crontabs/**my username**: Permission denied
crontab: error renaming crontabs/tmp.N9ZzvD to crontabs/**my username**
rename: Operation not permitted
```Anybody out there have any idea how I can fix this?

Thanks!

---

### Post by wadam on 2010-05-23
I hate to do it, but:  bump.

---

### Post by toates on 2010-06-13
hey,
not sure if it will be too helpful but i had some problems with BIT holding the destination of snapshots so i checked the config file at:
/home/***user***/.config/backintime/config
i would make sure these settings look right
Might try running backintime-gnome as sudo to see if it is a true permissions issue, not sure how helpful it would be though

---

