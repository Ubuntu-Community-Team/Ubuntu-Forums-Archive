---
title: "Crontab won't run"
date: 2009-12-03
forum: General Help
---

### Post by Kruptein on 2009-12-03
I've tried several things but none of them worked...:

I wont to run a simple shell script which runs perfectly in terminal, but not with crontab
I tried gnome-schedule,crontab -e but they won't run

the cron file:
* * * * * change_desktop.sh

I also tried with a full path: /usr/local/bin/change_desktop.sh
but that won't work either :(
If I use system wide crontab I do insert my account name between the stars(*) and the command...
 
/var/log/syslog
> esktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:37:01 linux-ubuntu CRON[10134]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:38:01 linux-ubuntu CRON[10146]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:39:01 linux-ubuntu CRON[10160]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec  3 15:39:01 linux-ubuntu CRON[10165]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:40:01 linux-ubuntu CRON[10181]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec  3 15:40:01 linux-ubuntu CRON[10182]: (darragh) CMD (/usr/local/bin/change_desktop.sh)
Dec  3 15:40:01 linux-ubuntu CRON[10204]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:41:01 linux-ubuntu CRON[10241]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:42:01 linux-ubuntu CRON[10265]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:43:01 linux-ubuntu CRON[10279]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:44:01 linux-ubuntu CRON[10299]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:45:01 linux-ubuntu CRON[10317]: (darragh) CMD (/usr/local/bin/change_desktop.sh)
Dec  3 15:45:01 linux-ubuntu CRON[10318]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:46:01 linux-ubuntu CRON[10342]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:47:01 linux-ubuntu CRON[10359]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:48:01 linux-ubuntu CRON[10370]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:49:01 linux-ubuntu CRON[10382]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:50:01 linux-ubuntu CRON[10396]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:50:01 linux-ubuntu CRON[10397]: (darragh) CMD (/usr/local/bin/change_desktop.sh)
Dec  3 15:51:01 linux-ubuntu CRON[10462]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:52:01 linux-ubuntu CRON[10474]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:53:01 linux-ubuntu CRON[10485]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:53:29 linux-ubuntu init: cron main process (10116) killed by TERM signal
Dec  3 15:53:29 linux-ubuntu cron[10500]: (CRON) INFO (pidfile fd = 3)
Dec  3 15:53:29 linux-ubuntu cron[10501]: (CRON) STARTUP (fork ok)
Dec  3 15:53:29 linux-ubuntu cron[10501]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Dec  3 15:53:32 linux-ubuntu init: cron main process (10501) killed by TERM signal
Dec  3 15:53:32 linux-ubuntu cron[10508]: (CRON) INFO (pidfile fd = 3)
Dec  3 15:53:32 linux-ubuntu cron[10509]: (CRON) STARTUP (fork ok)
Dec  3 15:53:32 linux-ubuntu cron[10509]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Dec  3 15:54:01 linux-ubuntu CRON[10512]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:55:01 linux-ubuntu CRON[10525]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:55:01 linux-ubuntu CRON[10528]: (darragh) CMD (/usr/local/bin/change_desktop.sh)
Dec  3 15:56:01 linux-ubuntu CRON[10547]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:56:54 linux-ubuntu /usr/bin/crontab[10560]: (darragh) LIST (darragh)
Dec  3 15:57:01 linux-ubuntu CRON[10565]: (darragh) CMD (/usr/local/bin/change_desktop.sh >> /dev/null 2>&1 # JOB_ID_1)
Dec  3 15:57:03 linux-ubuntu /usr/bin/crontab[10572]: (darragh) LIST (darragh)
Dec  3 15:57:03 linux-ubuntu /usr/bin/crontab[10576]: (darragh) REPLACE (darragh)
Dec  3 15:57:03 linux-ubuntu /usr/bin/crontab[10578]: (darragh) LIST (darragh)
Dec  3 15:57:07 linux-ubuntu init: cron main process (10509) killed by TERM signal
Dec  3 15:57:07 linux-ubuntu cron[10589]: (CRON) INFO (pidfile fd = 3)
Dec  3 15:57:07 linux-ubuntu cron[10590]: (CRON) STARTUP (fork ok)
Dec  3 15:57:07 linux-ubuntu cron[10590]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Dec  3 15:57:40 linux-ubuntu init: cron main process (10590) killed by TERM signal
Dec  3 15:57:40 linux-ubuntu cron[10595]: (CRON) INFO (pidfile fd = 3)
Dec  3 15:57:40 linux-ubuntu cron[10596]: (CRON) STARTUP (fork ok)
Dec  3 15:57:40 linux-ubuntu cron[10596]: (CRON) INFO (Skipping @reboot jobs -- not system startup)
Dec  3 15:58:01 linux-ubuntu CRON[10600]: (darragh) CMD (change_desktop.sh # JOB_ID_1)
Dec  3 15:59:01 linux-ubuntu CRON[10621]: (darragh) CMD (change_desktop.sh # JOB_ID_1)
Dec  3 16:00:01 linux-ubuntu CRON[10640]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Dec  3 16:00:01 linux-ubuntu CRON[10642]: (darragh) CMD (/usr/local/bin/change_desktop.sh)
Dec  3 16:00:01 linux-ubuntu CRON[10648]: (darragh) CMD (change_desktop.sh # JOB_ID_1)
Dec  3 16:00:01 linux-ubuntu CRON[10643]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Dec  3 16:00:03 linux-ubuntu /usr/bin/crontab[11657]: (root) LIST (nobody)


Help :D

---

### Post by Kruptein on 2009-12-03
I finally found the solution =D
after two days looking trough all the ubuntuforums posts I found this:
[http://ubuntuforums.org/showthread.php?t=1147321](http://ubuntuforums.org/showthread.php?t=1147321)
the last 2 - 3 posts did it

---

