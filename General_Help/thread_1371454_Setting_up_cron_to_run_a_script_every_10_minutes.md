---
title: "Setting up cron to run a script every 10 minutes"
date: 2010-01-03
forum: General Help
---

### Post by Colonel Forbin on 2010-01-03
I'm trying to get my cron to change my wallpaper every ten minutes. This is my first experiment with cron, so I'm not sure my code is right. Here's what I have

 /etc/crontab: system-wide crontab
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
10 * * * * root ~/changer
20 * * * * root ~/changer
30 * * * * root ~/changer
40 * * * * root ~/changer
50 * * * * root ~/changer
00 * * * * root ~/changer
#

When I try to then start the cron deamon it tells me Can't lock /var/run/crond.pid, otherpid may be 1333: Resource temporarily unavailable.

---

### Post by Barriehie on 2010-01-03
> **Colonel Forbin said:**
> I'm trying to get my cron to change my wallpaper every ten minutes. This is my first experiment with cron, so I'm not sure my code is right. Here's what I have

 /etc/crontab: system-wide crontab
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
10 * * * * root ~/changer
20 * * * * root ~/changer
30 * * * * root ~/changer
40 * * * * root ~/changer
50 * * * * root ~/changer
00 * * * * root ~/changer
#

When I try to then start the cron deamon it tells me Can't lock /var/run/crond.pid, otherpid may be 1333: Resource temporarily unavailable.

Should look something like this:
```

# m h dom mon dow user	command
0,10,20,30,40,50 * * * * root ***command***
```
Now, is ~/changer in your home dir or roots?

---

### Post by chewearn on 2010-01-03
If you are scheduling a task for the current user rather than root, it might be better to run crontab for the user only.

More info:
```

man crontab

```

I find it easier to use a GUI front-end, gnome-schedule; so I don't need to remember the details of crontab.

```

sudo apt-get install gnome-schedule

```

---

### Post by Colonel Forbin on 2010-01-03
~/changer is in my home directory. Should I then have user as forbin, or will root still be able to execute it? as for gnome-schedule, I think I have it programmed right, but still no change of wallpaper.

---

### Post by Barriehie on 2010-01-03
> **Colonel Forbin said:**
> ~/changer is in my home directory. Should I then have user as forbin, or will root still be able to execute it? as for gnome-schedule, I think I have it programmed right, but still no change of wallpaper.

```

# m h dom mon dow user	command
0,10,20,30,40,50 * * * * root /PathToCommand/Command

```

i.e.```
0,10,20,30,40,50 * * * * root /home/forbin/command
```

FWIW I never could get gnome-schedule to do anything on my machine.

Edit: When you're logged in does it work? either from the terminal or via the mouse?  If so, you can run it as you instead of root.

---

### Post by Colonel Forbin on 2010-01-03
> **Barriehie said:**
> ```

# m h dom mon dow user	command
0,10,20,30,40,50 * * * * root /PathToCommand/Command

```

i.e.```
0,10,20,30,40,50 * * * * root /home/forbin/command
```

FWIW I never could get gnome-schedule to do anything on my machine.

Edit: When you're logged in does it work? either from the terminal or via the mouse?  If so, you can run it as you instead of root.

changed my code to look just like that with the exception of command being changer. no joy. I can go into a terminal and run ~/changer and it works.

---

### Post by Colonel Forbin on 2010-01-03
After adding my wallpapers folder to the mouse change background command works.
but cron still does nothing

---

### Post by Barriehie on 2010-01-03
What does your cron log say?

Edit: Cron will update every minute and then you might have to wait for the length of time you have in your screensaver timeout before anything happens, i.e. no activity for x minutes.

---

### Post by chewearn on 2010-01-03
Since you are running with root rather than your user, you need to take care of the environments of your script; such as HOME, USER, PWD.

If you need to confirm whether the script is being executed, you could insert logger command in the script to output statuses into the system log.

---

### Post by Barriehie on 2010-01-03
> **chewearn said:**
> Since you are running with root rather than your user, you need to take care of the environments of your script; such as HOME, USER, PWD.

If you need to confirm whether the script is being executed, you could insert logger command in the script to output statuses into the system log.

+1, or redirect them into a $HOME/*file*  I have a 'jobs' folder in my $HOME that I use for testing scripts.

---

### Post by rnerwein on 2010-01-03
hi
Can't lock /var/run/crond.pid - this will tell you that cron is already runing.
you should use: crontab -u your_user file (or or or - see "man crontab"
see also /var/log/syslog to see what cron would tell you
ciao

---

### Post by Colonel Forbin on 2010-01-03
solved it. my original syntax was 0,10,20,30,40,50 * * * * root ~/changer

needed to be 0,10,20,30,40,50 * * * * root changer ~/changer

---

### Post by Barriehie on 2010-01-03
> **Colonel Forbin said:**
> solved it. my original syntax was 0,10,20,30,40,50 * * * * root ~/changer

needed to be 0,10,20,30,40,50 * * * * root changer ~/changer

Doh! Homer Simpson thing!  cront syntax of USER COMMAND

---

