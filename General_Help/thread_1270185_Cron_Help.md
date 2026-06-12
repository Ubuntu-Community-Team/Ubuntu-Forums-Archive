---
title: "Cron Help?"
date: 2009-09-19
forum: General Help
---

### Post by Raven917 on 2009-09-19
Hi I am having trouble getting cron to execute a script. 
(using duplicity for backups in conjunction with dropbox, its working quite nicely manually.)

The script works manually but when it is set for cron to run it nothing happens. 
Could any offer some assistance ??
Here is my script

[PHP]
#!/bin/bash

mysqldump -u root -p Mypassword --all-databases --single-transaction --delete-master-logs > /var/log/mysql/mysql_hourly-`date +%m-%d-%y`.sql


export PASSPHRASE=Mypassphrase

GPG_KEY=Mykey

duplicity -v8 --exclude=/sys --exclude=/dev --exclude=/proc --exclude=/tmp --exclude=/root/.dropbox --exclude=/root/Dropbox / file:///root/Dropbox/Backups

duplicity remove-all-but-n-full 1 -v8 --force file:///root/Dropbox/Backups

rm -rf /var/log/mysql/mysql_hourly-`date +%m-%d-%y`.sql

[/PHP]
I am running it as root and permissions is 755.

My crontab is
```

# m h  dom mon dow   command
  0 0,12 * * * /root/backup.sh &> /dev/null

```

What I hope I have set that to is run at 12:00/00:00 everyday and not to email me. 
So far I checked and most places say to check /var/adm/cron/log  but that doesn't exist (It didnt email me either that is why I set it to no email anyway) 

Any help ?  I have tried start/restarting and rebooting and nothing has worked so far.

---

### Post by Raven917 on 2009-09-19
8 hours long enough for a bump?

---

### Post by Raven917 on 2009-09-21
Bump again I guess?

---

### Post by SuaSwe on 2009-09-21
Have you checked whether your syslogs note the attempt to run the job? 

Also, have you experimentally tried placing the script in a different folder and/or changing the time to only once every 24 hours? Would be curious to know whether either would work!

---

### Post by badger_fruit on 2009-09-21
```
25 13 * * * /home/badger_fruit/automysqlbackup.sh.2.5
```
This runs at 13:25 every day ... like the previous post says, check your /var/log/messages to see what's happening.

I suggest that you set the job to run in a few minutes from "now" and then:-

```
sudo tail -f /var/log/messages | grep cron
```

You can watch then in real time what is outputted, hopefully you will find the problem for it not running.

---

### Post by Raven917 on 2009-09-23
> **SuaSwe said:**
> Have you checked whether your syslogs note the attempt to run the job? 

Also, have you experimentally tried placing the script in a different folder and/or changing the time to only once every 24 hours? Would be curious to know whether either would work!

I have tried placing it in different folders and setting it to only run at 00:00 everyday and sadly still no luck =[

> **badger_fruit said:**
> ```
25 13 * * * /home/badger_fruit/automysqlbackup.sh.2.5
```This runs at 13:25 every day ... like the previous post says, check your /var/log/messages to see what's happening.

I suggest that you set the job to run in a few minutes from "now" and then:-

```
sudo tail -f /var/log/messages | grep cron
```You can watch then in real time what is outputted, hopefully you will find the problem for it not running.

As for my logs this is what it says. /log/syslog
> 
Sep 23 00:00:01 Furan /USR/SBIN/CRON[24647]: (root) CMD (root /root/backup.sh &> /dev/null)

Sep 23 00:09:02 Furan /USR/SBIN/CRON[24651]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

Sep 23 00:17:01 Furan /USR/SBIN/CRON[24658]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 23 00:29:10 Furan -- MARK --


-it repeats this at 12 and 00 everyday. 

The messages log shows 
> 
Sep 21 00:08:39 Furan -- MARK --
Sep 21 00:28:39 Furan -- MARK --
Sep 21 00:48:39 Furan -- MARK --
Sep 21 01:08:40 Furan -- MARK --
Sep 21 01:28:40 Furan -- MARK --
Sep 21 01:48:40 Furan -- MARK --


this repeats every hour.

Thanks for your help so far... and tbh I cant understand what the log says.

---

### Post by DaithiF on 2009-09-24
Hi, i would suggest either have cron mail you the output from the job, or if you haven't got a mail transfer agent installed then redirect stdout & stderr output to a log file, like so:
```
* * * * * /root/backup.sh > /root/cron.log 2>&1
```
(note that the shorthand &> redirection of both stdout and stderr doesn't seem to work for me under cron, so I use the form above.)
Then take a look at the log after the job has run to see what error(s) have occurred.  you may want to add echo logging statements at various points in your script while you're investigating.

---

### Post by Raven917 on 2009-09-26
Well this is what the log says

> 
/root/backup.sh: line 10: duplicity: command not found
/root/backup.sh: line 12: duplicity: command not found
Yet when I do a manual duplicity it runs perfectly fine.

---

### Post by DaithiF on 2009-09-26
your $PATH is not the same as the PATH that is set when cron runs.  by default cron uses a path of /bin:/usr/bin I believe.  easiest thing is to make the path to duplicity explicit in your script.

```
which duplicity

```
to find out where it is located, then use that full path in your script
```
/path/to/duplicity -v8 etc...
```

---

### Post by Raven917 on 2009-09-28
Mate that worked like a charm. Thank you so much.

---

