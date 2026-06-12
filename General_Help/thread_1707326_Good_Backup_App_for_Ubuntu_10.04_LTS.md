---
title: "Good Backup App for Ubuntu 10.04 LTS"
date: 2011-03-15
forum: General Help
---

### Post by Peter Alien on 2011-03-15
I heard that Simple Backup 0.10.4 has bugs that doesn't allow it to create backups or replace them well.

I'm using Ubuntu 10.04 LTS.

Is it true?

If so, what do you advise me to run in my Server to create regular backups of my shared folders with Win7 machines?
I want it to make full backups not incremental ones if possible.
Oh and it has to be free, because i have to use it in a small enterprise.


Many thanks in advanced.

---

### Post by sedawk on 2011-03-15
There is an open source solution called "amanda" that
has been around for a long time. Check it out.

For simple "online-backup" to additional disks
I use rsync.
E.g. if you enter the backup disk "monday" on every Monday
and "rsync" your shared drive with the backup disk, only
the changes since last monday will be transferred.

There is also a way to use rsync in a mode that is
similar to Apples TimeMachine idea. What you
do is creating a new directory every day, e.g.
today you create 20110315 today you create 20110316, ...
Rsync has a special mode so it will use lots of
hardlinks in the new directory 20110315 pointing to the 
directory from yesterday if a file hasn't changed on the
shared drive. When browsing through 20110315 it will look
like a full backup although it actually is an incremental
backup.

---

