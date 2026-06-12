---
title: "changing fb background cronjob"
date: 2011-06-06
forum: General Help
---

### Post by st0ne2thedge on 2011-06-06
I'm trying to change my desktop background on my fluxbox desktop every minute using cronjob to a random picture within my Pictures folder
this is crontab -e file;
```

# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
* * * * * /usr/bin/fbsetbg -r /home/st0ne2thedge/Pictures > /home/st0ne2thedge/.cronLogs/fbsetRandomBackGround.sh.log

```
It's not doing anything though, the output file is created.
The command itself works when run in terminal works.

---

### Post by matt_symes on 2011-06-06
Hi

You need to use the display variable so it knows which display to use.

Try this.

```

# m h  dom mon dow   command * * * * * DISPLAY=:0 /usr/bin/fbsetbg -r /home/st0ne2thedge/Pictures > /home/st0ne2thedge/.cronLogs/fbsetRandomBackGround.sh.log
```

Kind regards

---

### Post by st0ne2thedge on 2011-06-06
> **matt_symes said:**
> Hi

You need to use the display variable so it knows which display to use.

Try this.

```

# m h  dom mon dow   command * * * * * DISPLAY=:0 /usr/bin/fbsetbg -r /home/st0ne2thedge/Pictures > /home/st0ne2thedge/.cronLogs/fbsetRandomBackGround.sh.log
```

Kind regards

Thanks, it is working now!

---

