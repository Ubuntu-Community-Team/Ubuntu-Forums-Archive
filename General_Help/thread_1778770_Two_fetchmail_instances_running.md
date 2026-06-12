---
title: "Two fetchmail instances running"
date: 2011-06-09
forum: General Help
---

### Post by martinrame on 2011-06-09
Hi, today I noted that my mail client (mutt) was showing each email received since yesterday repeated, then I did a "ps ax|grep fetchmail" and noted that I had this:


```
 1979 ?        Ss     0:00 /usr/bin/fetchmail -f /etc/fetchmailrc --pidfile /var/run/fetchmail/fetchmail.pid --syslog
 2841 ?        Ss     0:00 fetchmail -k
```

Shouldn't be only one fetchmail process running?.

I killed the process number 2841 and the wrong behavior disappeared.

After that, I found that I have two fetchmail scripts, one in /etc/default and the oher in /etc/init.d.  Is this ok?.

P.S.: I'm running Ubuntu 11.04 - x86_64

---

