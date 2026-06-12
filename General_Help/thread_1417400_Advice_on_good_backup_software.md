---
title: "Advice on good backup software?"
date: 2010-02-27
forum: General Help
---

### Post by jgfoot on 2010-02-27
I'm looking for advice on a good backup solution.  I have a couple Ubuntu machines running at home, and I'd like them to backup to a NAS, which supports CIFS and NFS.

rsync might work, but I don't want to have to write a script myself, or figure out how to accomplish a staggered history of backups.

The default "simple backup" sbackup doesn't work for me.  I've not been able to unroll those gigantic .tgz files it makes.  The restore GUI doesn't seem to work at all; it claims it can't find any backups.  My confidence is shot.

I tried Back in Time.  I set the GUI control panel to backup every day.  It didn't back up every day.  Maybe I'm getting it wrong.  But, my confidence is shot.

I looked at Amanda and Bacula.  Both seem to require that your backup server run special software; I don't want to hack into my NAS to do that.  Both also seem to require 10 hours of study to figure out just how to install them.

Any suggestions?

---

### Post by Wharf Rat on 2010-02-27
Jgfoot,
We seem to be in the same boat.  I have searched for an answer for months with similar results as you.

Perhaps someone will correct my dismal outlook but, I find that you really need a NAS that supports rsync.   Mine does not.   However, I have taken my laptop to work and backed up to my home directory on my work system as it runs rsync services.   Also, with a GOOD pipeline, I have run rsync from home to work.

I know that isn't what you asked for but it has been the most stable for me.

Also, I have tried Conduit which DOES mount my local NAS and seems to sync my music files.  But, some have mysteriously disappeared so I do not trust it.  Also, it crashes easily and you have to kick it off manually.  Not impressive.

So far, rsync seems to be the best engine --- as long as your server or NAS supports  it.  
Again at work - I use Deltacopy on Windows to back up my  PC to the server nightly - works great.  But is a Windows app.
My server (IBM Nitix) has a fantastic built in back up system that has never failed me.    I wish their back up routines could be ported to the desktop world.  I would gladly pay for it.

Sorry to not offer any real solutions for you. Nor did  I mean to hijack your thread.

Good luck.

---

### Post by ushills on 2010-02-27
i would use rdiff-backup as it is really easy to restore from, deja dup is simple and can backup to another mount point or via ssh i believe.  best to try a few.

---

