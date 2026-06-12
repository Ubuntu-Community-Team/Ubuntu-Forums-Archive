---
title: "&quot;locate&quot; doesn't work"
date: 2009-09-01
forum: General Help
---

### Post by viking_maniac on 2009-09-01
Last time I tried Ubuntu, I learned the *locate* command. It easily finds files stored on your computer and show their location.

When I use this command now, it finds only some files. It seems like the newest files are not found.

After a little research I found the database/index file that *locate* uses:
/var/lib/mlocate/mlocate.db
When I look at the properties of this file, it was last modified when I installed Ubuntu.

In SYSTEM -> ADMINISTRATION -> SERVICES, I turned off two *computer activity logger* services. Could this have something to do with the locate doesn't update itself and hasn't done this since the install of the OS?

---

### Post by PGScooter on 2009-09-01
I wonder if this is the same as a problem I had:

[https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/382330](https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/382330)

---

### Post by DaithiF on 2009-09-01
mlocate's db is updated by a cronjob in /etc/cron.daily/mlocate
Are the services:
Actions Scheduler (anacron)
and 
Actions Scheduler (cron)
set to run in your Services list?

---

### Post by andrew.46 on 2009-09-01
Hi viking_maniac,

If you were interested in an application that searches your drive *directly* rather than accessing a database you could do worse than to learn a little about find:

find - Ubuntu Community Documentation
[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

All the best,

Andrew

---

### Post by sedawk on 2009-09-01
You can run updatedb from the command line to update the database used
by locate.
```

sudo updatedb

```
should do the trick.

On the other hand the database should be updated on a daily basis - 
there is a cronjob /etc/cron.daily/mlocate that should run daily
to do it.

---

### Post by philinux on 2009-09-01
> **sedawk said:**
> You can run updatedb from the command line to update the database used
by locate.
```

sudo updatedb

```
should do the trick.

On the other hand the database should be updated on a daily basis - 
there is a cronjob /etc/cron.daily/mlocate that should run daily
to do it.

+1 I always use sudo updatedb before using locate.

---

