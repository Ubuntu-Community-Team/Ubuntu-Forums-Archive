---
title: "Nightly complaints from /etc/cron.daily/popularity-contest"
date: 2012-07-25
forum: General Help
---

### Post by ArlieS on 2012-07-25
I'm getting the following mailed to me/root/nobody daily.  

----------
Subject: Anacron job 'cron.daily' on xxxxx

/etc/cron.daily/popularity-contest:
/etc/cron.daily/popularity-contest: 18: .: Can't open
+/etc/popularity-contest.conf
run-parts: /etc/cron.daily/popularity-contest exited with return code 2
-----

This is a System76 machine, preinstalled with Ubuntu 12.04, on which I've done "apt-get update" and "apt-get upgrade", as well as some probably equivalent things via the GUI, but never touched the "popularity contest" as far as I can remember. 

The biggest relevant difference between this and a bog-standard workstation installation is that I've installed the postfix MTA. I don't think there was any MTA on the box when I received it; it gave me "connection refused" when I telnetted to what I think was the appropriate port on localhost. So it's quite conceivable that all workstation installations have a failing anacron job, but most can't deliver their complaints.

---

### Post by Cheesehead on 2012-07-25
Take a look at this possibly-related bug report: [https://bugs.launchpad.net/ubuntu/+source/popularity-contest/+bug/707311](https://bugs.launchpad.net/ubuntu/+source/popularity-contest/+bug/707311)

If you think you have the same issue, try:
```
sudo dpkg-reconfigure popularity-contest
```

---

### Post by ArlieS on 2012-07-25
That certainly looks like the problem I'm having. I've done the dpkg-reconfigure; I'll find out tomorrow (for sure) whether it worked.

Thank you.

---

