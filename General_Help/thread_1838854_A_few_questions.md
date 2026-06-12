---
title: "A few questions"
date: 2011-09-04
forum: General Help
---

### Post by slimb on 2011-09-04
I've found that my /var/log/messages is empty and hasn't been touched since 5/29

> tmyoungjr@alpha:/var/log$ ls -la messages
-rw-r----- 1 syslog adm 0 2011-05-29 07:36 messages

rsyslogd is definitely running

> tmyoungjr@alpha:/var/log$ ps aux | grep -i syslog
syslog    1716  0.0  0.0  28800  1228 ?        Sl   11:49   0:00 rsyslogd -c4

thoughts?

I've also got a cronjob running that I can't seem to clear up and remove (mrtg is uninstalled):

> Sep  4 12:25:01 alpha CRON[3764]: (root) CMD (if [ -x /usr/bin/mrtg ] && [ -r /etc/mrtg.cfg ]; then mkdir -p /var/log/mrtg ; env LANG=C /usr/bin/mrtg /etc/mrtg.cfg 2>&1 | tee -a /var/log/mrtg/mrtg.log ; fi)

> tmyoungjr@alpha:/var/log$ sudo crontab -l
no crontab for root
tmyoungjr@alpha:/var/log$  crontab -l
no crontab for tmyoungjr
tmyoungjr@alpha:/var/log$ sudo crontab -u mrtg -l
crontab:  user `mrtg' unknown

Thanks for any assistance that can be provided!

---

### Post by slimb on 2011-09-04
Forgot to mention that I've tried re-installing rsyslog.

for the cron issue i'm fairly certain that this is leftover from my smokeping install (both smokeping and mrtg are not installed and were removed using 'remove' instead of 'purge')

---

### Post by Toz on 2011-09-04
> **slimb said:**
> I've found that my /var/log/messages is empty and hasn't been touched since 5/29

rsyslogd is definitely running

thoughts?
I don't believe the messages log file is being used anymore. Have a look at **/etc/rsyslog.d/50-default.conf** for a listing of the default log files.

> I've also got a cronjob running that I can't seem to clear up and remove (mrtg is uninstalled):
According to the package file listings ([http://packages.ubuntu.com/natty/i386/mrtg/filelist]("http://packages.ubuntu.com/natty/i386/mrtg/filelist")) there is an **/etc/cron.d/mrtg** file that is installed and probably wasn't removed without the purge command.

---

### Post by slimb on 2011-09-04
Thanks Toz.

Two questions, two answers!!

---

