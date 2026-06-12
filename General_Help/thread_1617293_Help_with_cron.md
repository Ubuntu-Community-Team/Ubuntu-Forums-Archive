---
title: "Help with cron"
date: 2010-11-09
forum: General Help
---

### Post by aktiwers on 2010-11-09
I have a VPS which I connect to via SSH.

I have a script I want to run every day at a specific time, so I put this in my crontab:
```
01 04 * * * /root/startPyPing.sh

```

This however for some reason does not work. I suspect the problem is the same cause that made me want to create a cronjob at the first plays.

I want to run python script I have created, actually I want it running all the time. When logged in *** root via SSH I usually start this script manually. But when I logout, the script is stopped. Therefore I created an sh script to run the python script.

My thought was that cron then could run this script even though I am logged off, so I don't have to login daily to start it manually. 

Any suggestions how to make cron do this? Since the above does not work.

Or how I can test if cron is doing any hickups?

---

### Post by iponeverything on 2010-11-09
> **aktiwers said:**
> I have a VPS which I connect to via SSH.

I have a script I want to run every day at a specific time, so I put this in my crontab:
```
01 04 * * * /root/startPyPing.sh

```

This however for some reason does not work. I suspect the problem is the same cause that made me want to create a cronjob at the first plays.

I want to run python script I have created, actually I want it running all the time. When logged in *** root via SSH I usually start this script manually. But when I logout, the script is stopped. Therefore I created an sh script to run the python script.

My thought was that cron then could run this script even though I am logged off, so I don't have to login daily to start it manually. 

Any suggestions how to make cron do this? Since the above does not work.

Or how I can test if cron is doing any hickups?

see if anything is being reported /var/log/syslog

you can also add some debugging to code to your script.

---

### Post by Hippytaff on 2010-11-09
Standard stuff- but make sure the path is correct and the file name (I notice that you have it as .sh - is the python file saved as .py?)
 
Also, I'm not sure about cron running jobs while your logged off :-s

---

### Post by DaithiF on 2010-11-09
whose crontab -- yours or roots?  If yours, your user won't have access to /root so won't be able to run the script (unless you've changed the default permissions on /root)

---

### Post by aktiwers on 2010-11-11
This is all I see in syslog:

> Nov 11 07:35:01 myhostname anacron[2648]: Job `cron.daily' terminated (mailing output)
Nov 11 07:39:01 myhostname /USR/SBIN/CRON[2751]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Nov 11 07:45:01 myhostname anacron[2648]: Job `cron.monthly' started
Nov 11 07:45:01 myhostname anacron[2762]: Updated timestamp for job `cron.monthly' to 2010-11-11
Nov 11 07:45:01 myhostname anacron[2648]: Job `cron.monthly' terminated
Nov 11 07:45:01 myhostname anacron[2648]: Normal exit (2 jobs run)

Its a Debian server, and I currently only have a Root account.

The reason I have sh and py is because I was unsure if cron knew how to run python scripts, so I created a .sh script witch runs my python code:
cat /root/startPyPing.sh 
```

killall python3
python3 /var/www/pp/main.py

```

I run this script like mentioned in my first post - but loggin out of SSH seams to kill cron as well? Is there a way I can make sure cron runs even though root is logged out?

---

### Post by Cheesehead on 2010-11-11
If all you have is a root account, then your crontab line is incorrectly formatted...which also means you are probably putting it in the wrong crontab.

Root crontab is at /etc/crontab, and the format and rules are slightly different (and explained in the file - take a look).

User-level crontabs are edited using the 'crontab -e' command, and stored in /var/spool/cron. But they can only run user scripts, not root. The crontab you showed us looks like one of these, so it cannot run anything in /root.

Option: If it's a daily task, why not simply change the root crontab to run anacron's daily tasks at 4:01 (there's nothing magic about the default time), and then make your script just another daily task? This will ensure your job runs upon startup if the system happens to be down at that time, and will also run your task properly as root.

Cron can run just about any shell script, including launching python. But it's not smart about command names or user paths, so use the full path for a command.
Try '/usr/bin/python3 /var/www/pp/main.py' as the cron command.

I have launched python from cron jobs before, never launched one as a link from the /etc/cron.daily directory...but imagine it should be able to handle it as long as your python header (shebang line) is correctly set to '#!/usr/bin/python3'.

---

### Post by CharlesA on 2010-11-11
Use the full path to see if that helps.

---

### Post by aktiwers on 2010-11-15
> **Cheesehead said:**
> 

Option: If it's a daily task, why not simply change the root crontab to run anacron's daily tasks at 4:01 (there's nothing magic about the default time), and then make your script just another daily task? This will ensure your job runs upon startup if the system happens to be down at that time, and will also run your task properly as root.


Thanks Cheesehead, I decided to go with this method. I seam to be closer to my goal, I rebooted and the script did not run. Hereis my syslog:
```


:~# cat /var/log/syslog | grep cron
Nov 15 07:35:01 hostname anacron[4642]: Job `cron.daily' terminated (mailing output)
Nov 15 07:35:01 hostname anacron[4642]: Normal exit (1 job run)
Nov 15 12:39:01 hostname /usr/sbin/cron[1299]: (*system*) RELOAD (/etc/crontab)
Nov 15 12:39:50 hostname crontab[4877]: (root) LIST (root)
Nov 15 12:40:14 hostname crontab[4878]: (root) BEGIN EDIT (root)
Nov 15 12:40:26 hostname crontab[4878]: (root) REPLACE (root)
Nov 15 12:40:26 hostname crontab[4878]: (root) END EDIT (root)
Nov 15 12:40:28 hostname crontab[4880]: (root) LIST (root)
Nov 15 12:41:01 hostname /usr/sbin/cron[1299]: (root) RELOAD (crontabs/root)
Nov 15 13:14:01 hostname /usr/sbin/cron[1299]: (*system*) RELOAD (/etc/crontab)
Nov 15 13:14:11 hostname crontab[4895]: (root) LIST (root)
Nov 15 13:20:46 hostname crontab[4897]: (root) LIST (root)
Nov 15 13:23:51 hostname anacron[1280]: Anacron 2.3 started on 2010-11-15
Nov 15 13:23:51 hostname anacron[1280]: Normal exit (0 jobs run)
Nov 15 13:23:51 hostname /usr/sbin/cron[1300]: (CRON) INFO (pidfile fd = 3)
Nov 15 13:23:51 hostname /usr/sbin/cron[1301]: (CRON) STARTUP (fork ok)
Nov 15 13:23:51 hostname /usr/sbin/cron[1301]: (CRON) INFO (Running @reboot jobs)
Nov 15 13:30:53 hostname crontab[1356]: (root) LIST (root)
Nov 15 13:33:18 hostname crontab[1359]: (root) LIST (root)
Nov 15 13:33:51 hostname anacron[1275]: Anacron 2.3 started on 2010-11-15
Nov 15 13:33:51 hostname anacron[1275]: Normal exit (0 jobs run)
Nov 15 13:33:51 hostname /usr/sbin/cron[1295]: (CRON) INFO (pidfile fd = 3)
Nov 15 13:33:51 hostname /usr/sbin/cron[1296]: (CRON) STARTUP (fork ok)
Nov 15 13:33:51 hostname /usr/sbin/cron[1296]: (CRON) INFO (Running @reboot jobs)

```
Does this tell you anything? 

I can see it has not run, since I added :
```
echo "Startede Pyping: $(date)" >> /root/PyPingCron.log
```

And it is not creating any logs..

When rebooting to test if cron daily has run, do I have to wait until the defualt time of cron daily  6:25?
 
Sorry for being such an idiot about this - cron just don't fit into my brain :(

---

### Post by CharlesA on 2010-11-15
You can't run a script with an extension in cron.daily|monthly|hourly.

You'd have to create a link in there with no extension.

That applies to Debian and Ubuntu, but I'm not sure if it applies to other distros.

---

