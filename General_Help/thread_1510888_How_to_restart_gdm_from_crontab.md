---
title: "How to restart gdm from crontab"
date: 2010-06-16
forum: General Help
---

### Post by lunatico on 2010-06-16
Hello,

I'm having problems trying to restart gdm from crontab and I'm not sure what I'm doing wrong. Basically what I want to do is a 'logout' every morning before I get to work so that by the time I get to my computer I would just have to log back in and have a fresh gnome session.

The command I'm using to restart gdm is:
```
/usr/sbin/service gdm restart
```

If I run this command from a terminal as root it works.

To edit my crontab file I'm doing:
```
sudo crontab -u root -e
```

And adding the following line to it:
```
25 08 * * 1-5 /usr/sbin/service gdm restart
```

My understanding is that this should restart gdm every day of the work week (Mon-Fri) at 08:25. But for some reason this is not happening.

I also checked that my cron deamon is running by:
```
~$ service gdm status
gdm start/running, process 27156
```

Any help is much appreciated.

---

### Post by lunatico on 2010-06-17
I found a solution, not sure it's the best but it works.

Instead of using crontab -e and the service gmd commands I previously posted. Just edit the /etc/crontab file directly.

Backup the file:
```
sudo cp /etc/crontab /etc/crontab.bak
```

Edit it:
```
sudo vim /etc/crontab
```

Add the following line before the last line with a comment #
```
25 8	* * 1-5	root	/etc/init.d/gdm restart
```

So now the /etc/crontab file should look like this:
```
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
20 8	* * 1-5	root	/etc/init.d/gdm restart
#



```

If this is not the best solution or someone has a better one please post it.

---

### Post by dcstar on 2010-06-17
> **lunatico said:**
> 
.........
And adding the following line to it:
```
25 08 * * 1-5 /usr/sbin/service gdm restart
```

My understanding is that this should restart gdm every day of the work week (Mon-Fri) at 08:25. But for some reason this is not happening.
........

You should check your syslog file at that time to see what is happening.

---

### Post by lunatico on 2010-06-17
> **dcstar said:**
> You should check your syslog file at that time to see what is happening.

Yes I did and not apparent error.

This is the log output for the command that didn't work, on my first post.
Jun 17 08:25:01 mylaptop CRON[11648]: (root) CMD (/usr/sbin/service gdm restart # JOB_ID_1)

This is the log output for the command that did work, on my second post.
Jun 17 10:26:01 mylaptop CRON[25895]: (root) CMD (/etc/init.d/gdm restart)

Note that I also tried the command on the second post using the method on the first post.

---

### Post by lunatico on 2010-06-22
A work colleague gave me a brilliant tip on how to better do this.

Simply use the command:
```
DISPLAY=:0 gnome-session-save --force-logout
```

The beauty of this is that it can be run by the session user and not root. It's less invasive, it's like clicking 'log out' almost.

So to add this simply install (if you don't have it there already) gnome-schedule. Open it from Applications -> System Tools and create your task there with the above command.

---

### Post by lunatico on 2010-06-22
> **Joshua.Madison said:**
> Crontab is normally outside of your accessible area, if your isp gives  you access to it you had better read their instructions, that is the  only way you will gain access. I would never allow crontab access on any  of my web servers as this also creates a massive security hole for spam  email etc.

Thank you but how is this relevant to this thread? This is not on a webserver, it's just a personal desktop/laptop machine.

---

