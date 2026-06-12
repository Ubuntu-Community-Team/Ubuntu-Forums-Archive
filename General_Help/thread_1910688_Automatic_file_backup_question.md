---
title: "Automatic file backup question"
date: 2012-01-17
forum: General Help
---

### Post by chemnerd1 on 2012-01-17
Hey All,

I have a 64 bit Linux machine in lab and I need all files saved within a single folder to be automatically backed up. Initially I bought two 3Tb external hard drives and I tried to do a software RAID-1 mirror using the Disk Utility but I kept getting a partition misalignment error. 

So now I am just looking into ways to simply have all files saved within a specific folder be automatically saved onto one of the external drives. Is there a way to configure this in Ubuntu or do I need to use a backup utility? If the latter is there one you guys would recommend?

Thanks for the advice.

---

### Post by cortman on 2012-01-17
> **chemnerd1 said:**
> Hey All,

I have a 64 bit Linux machine in lab and I need all files saved within a single folder to be automatically backed up. Initially I bought two 3Tb external hard drives and I tried to do a software RAID-1 mirror using the Disk Utility but I kept getting a partition misalignment error. 

So now I am just looking into ways to simply have all files saved within a specific folder be automatically saved onto one of the external drives. Is there a way to configure this in Ubuntu or do I need to use a backup utility? If the latter is there one you guys would recommend?

Thanks for the advice.

Depends, I guess, if you need incremental backups or just a single copy of what is currently on the machine. For incremental backups, Deja Dup seems to have worked well for people. Otherwise it can be as simple as a "cp /stuff /backup" type script you can add to crontab.

---

### Post by chemnerd1 on 2012-01-17
Hey Cortman,

Thanks for the quick reply! 

I am brand spanking new to ubuntu so if I wanted to do the latter option is there a step-by-step tutorial you can link me to for adding that script? Sadly if there is no GUI then I need basic instructions :(

THanks again

---

### Post by oldfred on 2012-01-17
If anything there are too many options in Linux.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Besides just cp is rsync.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

---

### Post by pbrane on 2012-01-17
google for automatic backups using rsync and cron.
Here are a couple:
[http://linuxbasement.com/content/backups-using-rsync-bash-cron]("http://linuxbasement.com/content/backups-using-rsync-bash-cron")
[http://www.mikerubel.org/computers/rsync_snapshots/]("http://www.mikerubel.org/computers/rsync_snapshots/")
I came across this, never used it, don't know if its any good:
[http://www.liberiangeek.net/2011/03/setup-automatic-backup-ubuntu-fwbackups/]("http://www.liberiangeek.net/2011/03/setup-automatic-backup-ubuntu-fwbackups/")

Also there is grsync: [http://www.dedoimedo.com/computers/grsync.html]("http://www.dedoimedo.com/computers/grsync.html")

---

### Post by cortman on 2012-01-17
I haven't messed with rsync, so I'm probably missing something important there. But I have my /home folder backed up to a separate partition on my HD (which I have mounted in my filesystem as /data). My script is as simple as

```
rm /data/backup/*
cp -R /home/cortman /data/backup
```

Which simply removes all the previous contents of /backup and then copies all my files into /backup.

So it can be as simple as that, but some of oldfred's links look good. I'd recommend you look at them, and if you want a simple cp script I'd be happy to help with that too!

---

### Post by pbrane on 2012-01-17
> **cortman said:**
> I haven't messed with rsync, so I'm probably missing something important there. But I have my /home folder backed up to a separate partition on my HD (which I have mounted in my filesystem as /data). My script is as simple as

```
rm /data/backup/*
cp -R /home/cortman /data/backup
```

Which simply removes all the previous contents of /backup and then copies all my files into /backup.

So it can be as simple as that, but some of oldfred's links look good. I'd recommend you look at them, and if you want a simple cp script I'd be happy to help with that too!

With rsync you wouldn't need to delete the contents of the data directory. rsync will only copy new or changed files. It can also delete files that have been deleted on the filesystem.

---

### Post by cortman on 2012-01-18
> **pbrane said:**
> With rsync you wouldn't need to delete the contents of the data directory. rsync will only copy new or changed files. It can also delete files that have been deleted on the filesystem.

Sounds like a winner!

---

