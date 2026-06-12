---
title: "Making MySQL Run &quot;Nice&quot; Changing Priority Doesn't Work"
date: 2011-09-18
forum: General Help
---

### Post by fixitdude on 2011-09-18
I changed "nice = 19" (from zero) in /etc/mysql/my.cnf

Also tried "niceness=19" (was zero) in /usr/bin/mysqld_safe

And top still shows mysqld as running at nice of zero.

Anyone know what I am missing? I want to put it at a lower priority so it doesn't take up so much disk time and CPU. The function it does is nothing that has to be done right away.

Thanks in advance.

---

### Post by gmargo on 2011-09-18
The startup script, /etc/init/mysql.conf, runs the mysqld daemon directly.  It does not start the daemon through the mysqld_safe script, which is what that "nice" value applies to.

If you really want to do this (and I don't see why) you could edit that startup script to do so.

---

### Post by fixitdude on 2011-09-18
> **gmargo said:**
> The startup script, /etc/init/mysql.conf, runs the mysqld daemon directly.  It does not start the daemon through the mysqld_safe script, which is what that "nice" value applies to.

If you really want to do this (and I don't see why) you could edit that startup script to do so.Thanks, I'll try that.

The system is doing other more important things and when a mysql search is called, the disk I/O wait goes high enough to almost stop other processes.

If it used idle time to do it's thing, that would be OK in this situation because it has hours to do it and it's done from an automated script. It's not like I'm sitting there waiting for a result.

Is there a better or proper way to do this?

I wish there was a mysql command you could put on the query line for this, so that you could have the choice of which searches are more important CPU wise.


UPDATE:

For people who might want to do this, I added this to the /etc/init/mysql.conf script near the end, it now looks like this:
```

exec /usr/sbin/mysqld

post-start script

sleep 10
renice -n +19 -p `echo \`pgrep mysqld\` | sed -e 's/ /,/g'`
ionice -c 3 -p `echo \`pgrep mysqld\` | sed -e 's/ /,/g'`

    for i in `seq 1 30` ; do

```
It continues from there as it was...

This seems to work, it shows the "nice" priority as 19 and if you query the pid using ionice it shows it as set to "Idle", which means only use idle time.

If you wanted to make it a high priority just make the nice -19 and the ionice as 1 (for "real time"), or whatever numbers you want.


The question is there something / if something restarts mysqld, does it still use this script to re-start it?

---

