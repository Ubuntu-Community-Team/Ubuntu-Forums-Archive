---
title: "User crontab does not execute with cron.allow"
date: 2009-08-04
forum: General Help
---

### Post by kjiwa on 2009-08-04
I am using Ubuntu Server 8.04.3 LTS. I followed the instructions in the CronHowTo ([https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)) and added /etc/cron.allow and added my user name to the file. However, I'm still finding that my user crontab is not being executed.

Here is my crontab:

```
HOME=/home/kjiwa
PATH=$HOME/bin:$PATH
PERL5LIB=$HOME/lib/perl5

# m     h       dom     mon     dow     command
*       *       *       *       *       leslie-crontab.sh
```Here are some details about my system:

```
$ uname -a
Linux leslie 2.6.24-23-server #1 SMP Wed Apr 1 22:14:30 UTC 2009 x86_64 GNU/Linux

$ ls -l /etc/cron.{allow,deny}
ls: cannot access /etc/cron.deny: No such file or directory
-rw-r----- 1 root crontab 6 2009-08-04 14:38 /etc/cron.allow

$ whoami
kjiwa

$ sudo cat /etc/cron.allow
kjiwa
```

---

### Post by llamabr on 2009-08-04
I assume you're editing your cron with:

```
crontab -e
```

---

### Post by kjiwa on 2009-08-04
That's correct, I am editing my crontab with crontab -e

---

### Post by Glyndwr on 2009-08-04
A couple of things to check.

1. Is the cron daemon running:

$ ps -ef| grep cron

2. cron logs to syslog - are there any messages in /var/log/syslog about your script ?

---

### Post by kjiwa on 2009-08-04
Alright, thanks for your help. It looks like it's working, but I'm curious about the delay. The timestamp on cron.allow is 8 minutes before the first user cron command executed.

```

$ ls -l /etc/cron.allow
-rw-r----- 1 root crontab 6 2009-08-04 14:38 /etc/cron.allow

$ sudo grep leslie-crontab /var/log/cron.log | head -n5
Aug  4 14:46:01 leslie /USR/SBIN/CRON[5522]: (kjiwa) CMD (leslie-crontab.sh)
Aug  4 14:47:01 leslie /USR/SBIN/CRON[5547]: (kjiwa) CMD (leslie-crontab.sh)
Aug  4 14:48:01 leslie /USR/SBIN/CRON[5560]: (kjiwa) CMD (leslie-crontab.sh)
Aug  4 14:49:01 leslie /USR/SBIN/CRON[5571]: (kjiwa) CMD (leslie-crontab.sh)
Aug  4 14:50:01 leslie /USR/SBIN/CRON[5585]: (kjiwa) CMD (leslie-crontab.sh)

```

---

### Post by Glyndwr on 2009-08-04
The job will run for the first time after you did the 'crontab -e' - did you do that before or after adding your userid to cron.allow ?

---

### Post by kjiwa on 2009-08-04
I see. Yes, just before the first execution of my crontab, I notice entries in cron.log which indicate that I did edit the crontab.

It was a little confusing to me, but I think it makes sense. The cron daemon only loads up the user's crontab after it is sure that the user is allowed to execute cron jobs. Thus, somehow the user's crontab must be touched before it can be executed.

Do you think maybe it makes sense to add this to the wiki docs?

---

### Post by heykenen on 2009-08-05
I've the same problem.  Cron don't executa my job. There isn't cron.allow file in my system.  This is my cron.log


heiner@heiner-laptop:~$ more /var/log/cron.log
Aug  5 04:31:51 heiner-laptop crontab[13333]: (heiner) BEGIN EDIT (heiner)
Aug  5 04:32:09 heiner-laptop crontab[13333]: (heiner) REPLACE (heiner)
Aug  5 04:32:09 heiner-laptop crontab[13333]: (heiner) END EDIT (heiner)
Aug  5 04:33:01 heiner-laptop /usr/sbin/cron[10920]: (heiner) RELOAD (crontabs/h
einer)
Aug  5 04:40:01 heiner-laptop /USR/SBIN/CRON[13691]: (root) CMD ([ -x /usr/sbin/
update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug  5 04:41:01 heiner-laptop /USR/SBIN/CRON[13910]: (heiner) CMD (/usr/bin/stre
amrecord)

---

