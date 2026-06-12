---
title: "shutting off pc with cron"
date: 2010-01-25
forum: General Help
---

### Post by sr_guy on 2010-01-25
I'm trying to set up my pc to power off at 00:30 everynight. I'm using webmin's Scheduled Cron Jobs tool. I've tried (running as root):

halt
shutdown -h now

and neither have powered off the pc using webmin. Am I missing something?

---

### Post by squaregoldfish on 2010-01-25
You should find details of all attempted cron commands in /var/log/syslog.

Check the file around the time you set the cron job for (00:30) - are there any error messages?

Steve.

---

### Post by D3V11 on 2010-01-25
```

30 0 * * * shutdown

```

---

### Post by sr_guy on 2010-01-25
Here's the log after I add shutdown -h now in webmin:


Jan 25 11:50:01 KG /usr/sbin/cron[6537]: (asterisk) WRONG FILE OWNER (crontabs/asterisk)
Jan 25 11:50:01 KG /usr/sbin/cron[6537]: (root) RELOAD (crontabs/root)
Jan 25 11:50:02 KG /USR/SBIN/CRON[7642]: (root) CMD ([ -x /etc/init.d/mythtv-status ] && /etc/init.d/mythtv-status reload > /dev/null)
Jan 25 11:50:37 KG crontab[7762]: (root) BEGIN EDIT (root)
Jan 25 11:50:38 KG crontab[7762]: (root) REPLACE (root)
Jan 25 11:50:38 KG crontab[7762]: (root) END EDIT (root)

---

### Post by squaregoldfish on 2010-01-27
I'm afraid I don't know anything about webmin. However, you can put something like D3V11's line in /etc/crontab. Personally, I use the poweroff command, so I'd have the line:
```

30 00 * * * poweroff
```Once this is in your crontab file, you have to let the system know:

```
sudo crontab /etc/crontab
```That should do the job. If you want to use webmin, you'll have to figure out why the crontab files are throwing "wrong owner" errors - that would seem to be the cause of your problem.

Steve.

---

### Post by t4thfavor on 2010-01-27
Yup Poweroff will work, I have a workstation using it right now.

---

### Post by ducttapeandzipties on 2010-02-04
I am having the same problem right now,  I tried halt, shutdown and poweroff.  None of these work, and my /var/log/syslog shows no entry for these commands, it's as if cron is ignoring them completely.  

I am editing the crontab using "crontab -e" the line I am using is 

"55 06 * * * XXX"  

XXX being halt, shutdown or poweroff.

do I need to install this into the root's crontab?

---

### Post by squaregoldfish on 2010-02-04
Putting the command into root's crontab will work - the halt, shutdown and poweroff commands are root-only by default, for obvious reasons.

There are ways to make them accessible to all users, but I'm not sure if this is the right place for such discussions ;)

Steve.

---

### Post by tgalati4 on 2010-02-04
webmin is probably running with web priviledges--as user and group www-data.  You can either grant www-data shutdown priviledges or put the shutdown command in /etc/crontab which is the system crontab.  You can also put it in root's crontab:

sudo su
# crontab -e
(add your entries)

---

