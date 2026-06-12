---
title: "Backup Solutions?"
date: 2010-08-20
forum: General Help
---

### Post by dowanx on 2010-08-20
I am pretty new to using Ubuntu and want to find a way that I can backup files remotely to my Ubuntu box.  My Ubuntu box is running at work and I want to backup files from home automatically every night.

What solutions are available?  Also which solution encrypts the data en route?  Are there any solutions that would also allow my co worker to use it. For example a server with multiple clients with different directory paths.

I would like to find a good solution to this problem so I am asking you guys :).


Bryan

---

### Post by ScarletWyvern on 2010-08-20
rsync or ssh?

---

### Post by Ralph L on 2010-08-20
If you want a gui check out LuckyBackup and Deja Dup.  LuckyBackup allows more options, but Deja Dup is simpler to use.

---

### Post by jakupl on 2010-08-20
I really like[ CrashPlan]("http://b4.crashplan.com/landing/index.html"). It even supports backing up to cloud, unlimited storage. (free for 30 days, after that, it's a few bucks a month)
It was featured on the Linux Action Show a few days ago, that's where I found it.

---

### Post by Dragonbite on 2010-08-26
> **jakupl said:**
> I really like[ CrashPlan]("http://b4.crashplan.com/landing/index.html"). It even supports backing up to cloud, unlimited storage. (free for 30 days, after that, it's a few bucks a month)
It was featured on the Linux Action Show a few days ago, that's where I found it.

I'm looking at installing it on my home system, and including a dedicated "backup server" running linux.  Crashplan can be installed on a headless server.

I have 2 user-clients each dual-boot Linux and Windows (so 4 OS's) plus my server which I want to backup to the local backup server AND to the cloud.

Being able to backup locally is a benefit because[LIST=1]
[*]I can restore files so much faster from a local system than from online.  A guy from the computer club stored 160 GB online (Carbonyte?) and tested it by deleting his local version and restoring it.  The 160 GB took him 15 days to download.  A local version will be much, much faster.
[*]In case the online backup site goes down, is bought out, I decide to go elsewhere, etc. I still have a backup of my files in the local backup server.
[*]The local backup server could be a networked external hard drive, or to a portable/external hard disk that I can take with me and store elsewhere.
[*]The local backup can also be the OTHER computers being backed up instead of a dedicated server.
[/LIST]

First I'm hoping to set it up so they are backing up to the local server, then I'll look at pushing it up to the cloud.

Anybody have experience with this?  I know I could use rsync, Deja Dup, Back-in-Time, etc. but this sounds like the easiest to setup, configure and maintain.

---

