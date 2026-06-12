---
title: "syslog"
date: 2011-11-22
forum: General Help
---

### Post by techbrainless on 2011-11-22
Hi All,
I have checked  "/var/log/syslog" and it contains only the current month logs , it seems that it gets rotating monthly  , my questions are :
1. Is it possible to get the logs of the previous month using syslog or any other log.
2. How to configure syslog to be rotated in a user defined period (something like 2 months , 6 months or 1 year)

---

### Post by gmargo on 2011-11-22
See my answer in your other thread:
[http://ubuntuforums.org/showthread.php?t=1884906](http://ubuntuforums.org/showthread.php?t=1884906)

For syslog rotation, see the **/etc/logrotate.d/rsyslog** file.

---

