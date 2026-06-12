---
title: "Cron job not running"
date: 2009-12-11
forum: General Help
---

### Post by erict43 on 2009-12-11
I'm using wubi to run Ubuntu 9.10 on a Widows 7 machine (still need to work with both platforms).  I'm trying to set up a cron job to run every hour to log who is logged in to the system.  I'm testing it out on this machine before putting it on a Linux production server at work.

Both of my scripts run fine from the command line, I just can't get them to run automatically.  Here is what I did.

File /etc/cron.hourly/logins contains:
```
bash /home/eric/whoscript >> /home/eric/logins.log 2>&1
```


File /home/eric/whoscript contains:
```
#!/bin/sh
#
# whoscript - Script to count and list logged on users
#
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
echo "----------------------------------"
echo "Time: \c";date
echo "Number of users: \c"; who | wc -l
who
#
# End
```

My log file logins.log never gets created.  Can't figure it out.  syslog says that cron is running every hour.  Does just putting my script in cron.hourly make it run?  Any help is appreciated.

---

### Post by Greenwidth on 2009-12-11
I think Crontab is what you are looking for:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by erict43 on 2009-12-12
Well, I was able to make it work by using crontab -e and adding the line
```
55 * * * * /bin/bash /home/eric/whoscript >> /home/eric/logins.log 2>&1
```

I achieved my objective, but I still don't understand how to make cron.hourly work.  I thought that if you put a script in there, it will run hourly.  In this case it didn't.  Anyone know why?

---

### Post by daqron on 2009-12-15
Yes, I would like to know the answer to this as well. As of 9.10 I have an incredibly annoying bug where my system clock gains 2 minutes every few hours. My intended workaround is to add this cron file called ntpdate in the /etc/cron.hourly directory:

```
#!/bin/bash
ntpdate ntp.ubuntu.com
```
I added and saved the file, chmod to 755. Unfortunately the script doesn't seem to be running. I tried running crontab -l as root and as myself and it says "no crontab for [user]".

One thing that seems strange to me is that cron.hourly is treated differently than the other anacron parts. This is from /etc/crontab:

```
# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
```
I admit I don't understand what these entries are doing (other than, in theory, running all the scripts within each anacron directory) but why would the hourly one be different than the others?

Cheers,
Jeremy

---

### Post by airone1 on 2010-01-23
you can see which jobs should run with '$ sudo run-parts --test /etc/cron.hourly'

the man page of run-parts specifies some rules about the file names and perms required for the cron jobs, although you seem to respect them if the name of your cron job is something like "ntpdate" or "fixdate"

slightly out of topic: maybe the ntpd daemon would be a better solution (package: ntp), since it doesn't involve a so brute change of clock. some daemons may not like it...

---

### Post by airone1 on 2010-01-23
ps: the cron.hourly is managed differently because anacron takes care of running jobs which were supposed to run, but couldn't for various reasons (for example, the system was off, or in single mode, etc...). It does so by keeping an internal database of scheduled jobs and executions, doing its best to fulfil the requests.

It has some sense for jobs that don't have a chance to be re-called soon. If you have system that was off overnight, if anacron is asked to take care of the cron.hourly as well, it would call on startup the (say) 8 jobs not ran during the night: a spicy race condition (they would be running all at the same time *on the same files*)

---

### Post by daqron on 2010-05-14
Quick update -- I am having the same time drift problem in Lucid. I have the cron solution that I posted above in place and it works great. Thanks for the tip on "run-parts" - that was a good tool for testing.

---

### Post by roland-orre on 2011-10-03
It seems as there recently has been some change in allowed names. I used to name those scripts I put under e.g. cron.hourly  with suffix .sh 
 When I removed the suffix .sh then it worked fine.
  [QUOTE=daqron;8504707]Yes, I would like to know the answer to this as well.    
Thanks to airone1's hint about **run-parts --test** and **run-parts --list** I got this solved.   :grin:

---

### Post by oldos2er on 2011-10-03
Closed, necromancy.

---

