---
title: "Random restart"
date: 2011-06-20
forum: General Help
---

### Post by Dancin' Hamster on 2011-06-20
Hi,
In past few days, my ubuntu 11.04 restarts, it's only once per start, and happens when I press enter. Usually it's in first few minutes of running or sometimes after hours of running. Well it isn't full restart, just seems like gnome restart. I hope you know what I mean, here is part of my /var/log/syslog, this is when I think it happened:

```
Jun 20 14:04:18 pc rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="821" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jun 20 14:05:08 pc anacron[2645]: Job `cron.daily' terminated
Jun 20 14:05:08 pc anacron[2645]: Normal exit (1 job run)
Jun 20 14:08:55 pc AptDaemon: INFO: Quitting due to inactivity
Jun 20 14:08:55 pc AptDaemon: INFO: Shutdown was requested
Jun 20 14:09:01 pc CRON[4257]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete)
```

full syslog in attachment( 2 parts, beacuse of size limit)

well I am new here but I hope I provided all you need and thanks in advance for your help :)

---

