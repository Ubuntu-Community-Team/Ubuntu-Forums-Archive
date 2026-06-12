---
title: "Crons do not work"
date: 2009-08-06
forum: General Help
---

### Post by treesloth on 2009-08-06
So, I just installed Eeebuntu on my Eee PC yesterday.  It's a great installation and system, much like most Ubuntu-based dists, but there is one problem.  I wanted to get my wallpaper to change periodically.  I have a working script to randomly change it, but for some reason, crons aren't running.  I've done the following:

1)  Checked the output of [FONT="Courier New"]**ps auxww **[/FONT]for the cron binary.  It is running.
2)  Restarted cron anyway:

```
/etc/init.d/cron stop
/etc/init.d/cron start
```

3)  Set up a little token cron that should be pretty much bulletproof:

```
* * * * * /bin/date >> /tmp/dateout
```

The /tmp/dateout file doesn't get populated.  I even touched the file to make sure it wasn't a strange file creation problem.  I created the job using the command [FONT="Courier New"]**crontab -e**[/FONT] in both the user and root crons.  No luck on either.

Any suggestions?  This is a completely fresh installation.  I installed a fresh-from-assembly SSD (32GB... very fast... very nice...) with, obviously, no previous stuff.  I installed eeebuntu from a flash drive, ran system updates, then tried the cron setup.  I don't see how anything could possibly have snuck in to break it.  Please help.  With static wallpaper, my life is a desolate wasteland. :)

---

### Post by dcstar on 2009-08-07
> **treesloth said:**
> So, I just installed Eeebuntu on my Eee PC yesterday.  It's a great installation and system, much like most Ubuntu-based dists, but there is one problem.  I wanted to get my wallpaper to change periodically.  I have a working script to randomly change it, but for some reason, crons aren't running.
.......

```
crontab -l
```

If it is empty then there may be a permissions issue.

Try installing the Gnome Scheduler tool.

---

