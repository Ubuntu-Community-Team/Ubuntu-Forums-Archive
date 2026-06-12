---
title: "cron.daily .weekly .monthly  -  not working"
date: 2009-07-27
forum: General Help
---

### Post by cbear on 2009-07-27
I added several scripts to my cron.daily, cron.monthly and cron.weekly directories under /etc .  The existing jobs that were already there seem to run, but the scripts that I added do not.  I can run them manually, no problem.  They just don't get executed when in the pre-programmed directories.  I can also run them via cron if I enter my own cronjob line.  

Why is cron (or anacron) not executing my scripts that are placed in the .daily, .weekly and .monthly directories ?

thanks in advance

---

### Post by credobyte on 2009-07-27
Can you post the output of /var/log/syslog & what exactly you are trying to execute ( scripts ) ?

---

### Post by cbear on 2009-07-27
I created a test script in cron.daily .  Here is the script and the syslog:


file = etc/cron.daily/testscript  -  chmod +x = yes
tbegehr@LINUX03:~$ cat /etc/cron.daily/testscript 
#!/bin/sh

touch /home/backups/test.file





SYSLOG
tbegehr@LINUX03:~$ cat /var/log/syslog | grep cron
Jul 27 08:40:01 LINUX03 anacron[18170]: Job `cron.daily' terminated
Jul 27 08:40:01 LINUX03 anacron[18170]: Normal exit (1 job run)
Jul 27 09:00:01 LINUX03 /USR/SBIN/CRON[20114]: (list) CMD ([ -x /usr/lib/mailman/cron/disabled ] && /usr/lib/mailman/cron/disabled)
Jul 27 09:30:01 LINUX03 /USR/SBIN/CRON[20735]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 27 10:30:01 LINUX03 /USR/SBIN/CRON[21864]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 27 11:30:01 LINUX03 /USR/SBIN/CRON[23024]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 27 12:00:01 LINUX03 /USR/SBIN/CRON[23643]: (list) CMD ([ -x /usr/lib/mailman/cron/senddigests ] && /usr/lib/mailman/cron/senddigests)
Jul 27 12:30:01 LINUX03 /USR/SBIN/CRON[24315]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 27 13:30:01 LINUX03 /USR/SBIN/CRON[25581]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 27 14:30:02 LINUX03 /USR/SBIN/CRON[26773]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 27 15:30:01 LINUX03 /USR/SBIN/CRON[27953]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 27 15:36:01 LINUX03 /usr/sbin/cron[5659]: (*system*) RELOAD (/etc/crontab)
Jul 27 15:40:01 LINUX03 /USR/SBIN/CRON[28388]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))


The cron.daily ran at 15:40.  It is not 16:18 and there is no test.file in /home/backups.

I can run the script manually from /etc/cron.daily.  It does not seem to run along with the other .daily jobs.  In fact, I am not 100% sure the other jobs in .daily are running either.

I am not a linux expert, but not entirely a novice either.

thanks for your help :)

---

### Post by DaithiF on 2009-07-27
no, although cron ran @ 15:40, it just tested whether or not anacron is installed (it is), and then exited.  Basically cron is deferring to anacron to run everything in cron.daily|weekly|monthly

this post explains things quite well:
[http://ubuntuforums.org/archive/index.php/t-670293.html](http://ubuntuforums.org/archive/index.php/t-670293.html)

did your previous scripts contain periods, e.g. somescript.sh  -- per that thread that would have caused them not to be run.  Your more recent 'testscript' doesn't have a period in its name, and so probably **will** run next time anacron runs, which will be early morning by the looks of it (it finished at 08:40 this morning.)

cheers
d

---

### Post by cbear on 2009-07-27
That makes sense...thanks.  Where does anacron get it's time config information ?  How would I change the time ?

---

### Post by DaithiF on 2009-07-28
anacron itself is run (a) just after boot, and (b) daily by cron according to the time set in /etc/cron.d/anacron ... 7:30am for me.

---

