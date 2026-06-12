---
title: "Equivalent of Apple's Time Machine?"
date: 2012-01-10
forum: General Help
---

### Post by jkounis on 2012-01-10
Is there an equivalent of Apple's time machine available on Linux?

I have found some packages such as BackInTime, TimeVault, and FlyBack, but all seem to just be fancy graphical interfaces for  full and incremental backups, which I already know how to do using tar.

The key thing that Apple's Time Machine does that none of these packages seem to do is track _deleted_ files.

Let's take the following scenario:
[LIST=1]
[*]I create three files: A, B, C.
[*]I perform a full backup, which backs up A, B, C.
[*]I delete File B.
[*]I perform an incremental backup.
[*]I have a disk crash.
[/LIST]

In the case above, when I restore my full and incremental backups, I will end up with three files: A, B, and C. There is not information that file B has been deleted.

In order to work around the above problem, I started using rsync with the --delete option. The problem with this is that if I have a disk crash that causes the disk to unmount from the mount point immediately before the backup, then rsync thinks all the files have been deleted, so it dutifully erases my entire backup! (Also not a good choice.)

Is there any other solution for point-in-time recovery that takes into consideration deleted files?

---

### Post by jkounis on 2012-01-16
Just an update: After much searching, it looks like the command-line utility [rdiff-backup]("http://www.nongnu.org/rdiff-backup/") will do what I need. It keeps track of file deletions and makes a true incremental backup that can be restored to a point in time.

The only thing it does not do, which Apple's Time Machine does, is automatically erase old files as the backup volume fills up. You can use the --remove-older-than option to remove backups older than a certain time, e.g. 30 days or 1 week. However, there is no option to remove as many old files as are necessary to not fill up the backup volume, which is essentially what Apple's Time Machine does.

---

### Post by Cheesemill on 2012-01-16
I use [rsnapshot]("http://rsnapshot.org/") on my machines.

If you want a GUI you could also take a look at [Back in Time]("http://backintime.le-web.org/").

---

### Post by nortexoid on 2012-12-16
jkounis, thanks for all this useful information. I TM on my Mac but am looking for something on linux. Still too bad there isn't as nice a solution as TM for linux. I would even pay for it!

---

### Post by Zill on 2012-12-16
nortexoid:  You might like to take a look at [luckyBackup]("http://luckybackup.sourceforge.net/").

This is based on rsync but also keeps a specified number of snapshots so that you can easily restore an earlier backup.

---

### Post by ipina on 2013-01-26
Have you tried CrashPlan? As far as I know it's the most similar backup procedure to Apple's Time Machine. You can use it without spending money by ignoring CrashPlan Central. Cheers.

---

