---
title: "crontab &amp; setting something as service"
date: 2010-10-15
forum: General Help
---

### Post by vbSteve on 2010-10-15
Hi;


I've successfuly converted my windows server to an Ubuntu server (in console mode) and while everything is working well, I have 2 questions.

Yesterday I read through [the cron documentation](https://help.ubuntu.com/community/CronHowto) to see how to schedule a task, and applied that to create a daily reboot task at 6 am. So I ran this command *$ sudo crontab -e -u root* and added the following to the file:

```

# Daily reboot at 6 am:
0 6 * * * shutdown -r -time 0

# Monthly maintenance (at 1 am every first of the month):
# This includes cleaning logs, backing up websites, mysql and configurations
0 1 1 * * /var/maintenance.sh

```

This morning, as I was sure that it would've worked, I found the server still on-line (which was okay as it was suppose to reboot) with an uptime little over 19 hours, indicating the reboot task did not run.

Do I need to run an additional command before the new crontab configuration kicks in?



Second question is sort of a concern, I haven't tested it yet on the server, but on the desktop edition of ubuntu (in Virtual Box) I've installed steam dedicated server to run Team Fortress 2. It runs, but after I called in the command to launch the server, I get stuck in the steam dedicated server console until I *quit* it.  I suppose I could run a *screen -S tf2 ./srcds_run* to make it run in its own screen session, but can I automatically detach from it, so that after the steam server is launched, I get back to the linux terminal prompt?

I also would like to make it so - if I would install this on my server - that it runs automatically on system boot, so that I don't have to log on to the ssh and manually type in the command.  What's the best way to approach this? It would be cool if I can install the steam ds as a service (like apache2) so I can stop, start and restart it as I please with the service command or /etc/init.d or whatever.


Thanks :)


** Update **
Found out how you can automatically detach from screen command.

---

### Post by anglican on 2010-10-15
> **vbSteve said:**
> 
```

# Daily reboot at 6 am:
0 6 * * * shutdown -r -time 0

# Monthly maintenance (at 1 am every first of the month):
# This includes cleaning logs, backing up websites, mysql and configurations
0 1 1 * * /var/maintenance.sh

```

You usually need to give the full path to commands in crontab as cron doesn't give you the same environment as a logged in user. So try "/sbin/shutdown" instead.

> **vbSteve said:**
> Do I need to run an additional command before the new crontab configuration kicks in?
No


> **vbSteve said:**
> Second question ...Can't help with this one.

H

---

### Post by vbSteve on 2010-10-15
> **anglican said:**
> You usually need to give the full path to commands in crontab as cron doesn't give you the same environment as a logged in user. So try "/sbin/shutdown" instead.


Okay,  I'll give that a try. Thanks.

---

