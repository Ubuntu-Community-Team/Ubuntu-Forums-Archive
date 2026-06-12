---
title: "cron jobs stopped running"
date: 2011-06-02
forum: General Help
---

### Post by Aisling on 2011-06-02
I am running Ubuntu 10.10 on a new Dell PowerEdge.

I built the system ~2 months ago and have successfully been running a list of cronjobs.

The jobs last ran on 5/31/11 at 7:35am.  Since then none of the jobs have run.

I see "cron" in the process list when I run ps.

Any ideas what could cause this??

Thanks.

---

### Post by seawolf167 on 2011-06-02
Welcome to the forums!

First thing - double check that cron is running (yes I know you posted that it was - just double checking)

```
ps -ef | grep cron
```

should give you two entries, one for cron, one for the grep cron search

Can you post your crontab file from /etc/crontab in CODE tags for us to take a look at?

---

### Post by Aisling on 2011-06-02
Result:

root       990     1  0 Apr22 ?        00:00:07 cron
1000     17723 17492  0 10:19 pts/0    00:00:00 grep --color=auto cron

Not sure what you mean by CODE tags, but here is one line.  Most importantly, this has been operating w/o issues for over a month.

*/5 1-23 * * * php /home/gmorehead/web/SysMonitor/php/dataAggregator.php

---

### Post by wolfgangmcq on 2011-06-02
Does restarting the system help? I sometimes find that things get mixed up for no obvious reason, and restarting fixes it.

---

### Post by seawolf167 on 2011-06-02
There is a little button that looks like a pound symbol which makes code tags you can put code entries in to make the format a little nicer.

The crontab entry looks ok:
-does the user "php" have permission to execute the script in question? I know it worked before, but maybe an update/upgrade changed that file permissions?
-do your logs show anything?

I change so that cron logs to /var/cron.log instead:

edit

```
sudo gedit /etc/rsyslog.d/50-default.con
```

then uncomment the line

```
cron.*         /var/log/cron.log
```

does restarting the cron service help?

```
sudo service cron restart
```

---

### Post by Aisling on 2011-06-02
I was hesitant to restart the system w/o an answer.  I depend heavily on cron and need to be able to trust it.

I restarted cron and it is now working.

I've also enabled logging like you mentioned.  Will I need to reboot for it to actually take effect?

So the million dollar question is, what happened!

---

### Post by seawolf167 on 2011-06-02
You only need to restart the service in order to enable logging in the specified path (that you just modified). That is done via the same command as above

```
sudo service cron restart
```Essentially the only 2 times you need to restart your computer is for kernel updates and video card driver updates. All other times either a logout/login or very simple service restart will fix your issues.

No idea what happened - maybe an update/upgrade stopped the service for some reason? Maybe a job hung it? Not sure... you may be able to tell in the log files.

I wouldn't worry too much about it if it is an isolated incident - keep an eye on the log files /var/cron.log and make sure it is working properly; else you'll need to do some digging around in your system logs to see what is causing it to stop

---

### Post by Aisling on 2011-06-02
Ok.  Thanks for the help.

---

### Post by sanguinoso on 2011-06-02
I heard about an update to PAM that caused cron jobs to stop working. A restart to the cron service fixes the problem.

[https://bugs.launchpad.net/ubuntu/natty/+source/pam/+bug/790538](https://bugs.launchpad.net/ubuntu/natty/+source/pam/+bug/790538)

---

### Post by seawolf167 on 2011-06-02
> **Aisling said:**
> Ok.  Thanks for the help.

No problem - glad everything is working again!

---

