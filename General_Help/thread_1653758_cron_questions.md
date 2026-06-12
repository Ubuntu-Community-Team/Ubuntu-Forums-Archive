---
title: "cron questions"
date: 2010-12-27
forum: General Help
---

### Post by linuxwonder on 2010-12-27
Hi All:

I have 10.04 and I am trying to launch ant to do some overnight builds. my crontab -l is:

56 10 * * * /usr/bin/ant -f /home/myuser/GMRunner.xml >>/home/myuser 2>&1

ignore the actual time because these will change once I get this to work. My questions are:

If this is generating a log file, 


[LIST=1]
[*]where is it?
[*]what is its name?
[/LIST]
thanks

---

### Post by Cheesehead on 2010-12-27
The default in 10.10 is to log events to /var/log/syslog.
Try this command to see log entries by cron: cat /var/log/syslog | grep cron

To give cron its own logfile, edit /etc/syslog.conf (using sudo). You'll see the entry for cron commented out. Just take out the '#' and restart. Most users don't really need a separate cron logfile, grepping cron out of syslog is pretty easy.

Also, 'man cron' describes the three loglevels to choose from, and how to swithc between them: 0 - No log, 1 - log the begnning of a job, and 2 - log the beginning and end of a job.

---

### Post by linuxwonder on 2010-12-27
Thanks Cheesehead it looks good now!

---

