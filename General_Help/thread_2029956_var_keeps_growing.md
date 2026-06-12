---
title: "/var keeps growing"
date: 2012-07-20
forum: General Help
---

### Post by Statia on 2012-07-20
Hi all,

I have a Kubuntu 12.04 64-bit installation, with / on a SSD and /var on the HDD where /home also lives.  /var/spool , /var/tmp and /var/cache/apt/archives are in RAM, as tmpfs.
Originally I had allocated about a 800MB for /var, but this filled up pretty quickly. I was able to shuffle my partitions around a bit with gparted and resize /var to 1.2G, but it fills up the extra space in no time. I've done the obvious things like removing old logfiles (going to make that a cron-job) and apt-get clean and apt-get autoclean, but this only helps temporarily. What other options do I have? Preferably I'd have a solution that prevents /var from overflowing permanently, but I could live with some tips for culprits that could safely be deleted through a cron-job.

PS: Yes, having / on a SSD is bleeding fast :D

---

### Post by Statia on 2012-07-23
Did some digging and found a 127MB kern.log in /var/log. Forced a logrotate and removed the old logfiles. Changed settings to keep 2 weeks of logfiles instead of 4.

Nvidia keeps it's drivers (or a copy from install?) in /var/lib. Guess I reasonably will only need the driver for the previous kernel version at worst, so removed the rest.

/var back at 65% usage (from 100%), I'll see how it develops.
At least I identified some culprits.

---

### Post by Statia on 2012-10-01
What are al these .DB files in /var/cache/apt-xapian/index.1 ?

```
$ ls -l
total 87860
-rw-r--r-- 1 root root        0 Sep 30 15:45 flintlock
-rw-r--r-- 1 root root       28 Aug  8 14:51 iamchert
-rw-r--r-- 1 root root      653 Sep 30 15:45 postlist.baseA
-rw-r--r-- 1 root root      653 Sep 29 22:56 postlist.baseB
-rw-r--r-- 1 root root 43499520 Sep 29 11:54 postlist.DB
-rw-r--r-- 1 root root       53 Sep 30 15:45 record.baseA
-rw-r--r-- 1 root root       53 Sep 29 22:56 record.baseB
-rw-r--r-- 1 root root  2424832 Sep 29 11:54 record.DB
-rw-r--r-- 1 root root       82 Sep 30 15:45 spelling.baseA
-rw-r--r-- 1 root root       82 Sep 29 22:56 spelling.baseB
-rw-r--r-- 1 root root  5054464 Sep 29 11:54 spelling.DB
-rw-r--r-- 1 root root       14 Sep 30 15:45 synonym.baseA
-rw-r--r-- 1 root root       14 Sep 29 22:56 synonym.baseB
-rw-r--r-- 1 root root    16384 Sep 30 15:45 synonym.DB
-rw-r--r-- 1 root root      612 Sep 30 15:45 termlist.baseA
-rw-r--r-- 1 root root      612 Sep 29 22:56 termlist.baseB
-rw-r--r-- 1 root root 38912000 Sep 29 11:54 termlist.DB
```

This is responsible for most of the growth of /var, so it would be nice to know if I could either clean this out or curtail its growth.

---

### Post by Statia on 2012-10-01
> **Statia said:**
> Did some digging and found a 127MB kern.log in /var/log. 


There seems to be no entry for kern.log in either /etc/logrotate.conf or /etc/logrotate.d.
Should I make one myself?
Does anyone have suggestions for the options to use?

---

### Post by spjackson on 2012-10-01
On 2 of my systems (10.04 and 12.04) kern.log is catered for in /etc/logrotate.d/rsyslog which looks like this (12.04 version).
```

/var/log/syslog
{
    rotate 7
    daily
    missingok
    notifempty
    delaycompress
    compress
    postrotate
        reload rsyslog >/dev/null 2>&1 || true
    endscript
}

/var/log/mail.info
/var/log/mail.warn
/var/log/mail.err
/var/log/mail.log
/var/log/daemon.log
/var/log/kern.log
/var/log/auth.log
/var/log/user.log
/var/log/lpr.log
/var/log/cron.log
/var/log/debug
/var/log/messages
{
    rotate 4
    weekly
    missingok
    notifempty
    compress
    delaycompress
    sharedscripts
    postrotate
        reload rsyslog >/dev/null 2>&1 || true
    endscript
}

```

---

### Post by Statia on 2012-10-01
Thanks, I had not seen (or expected) kern.log in rsyslog.
Now I'll just have to check why it gets so big.

---

