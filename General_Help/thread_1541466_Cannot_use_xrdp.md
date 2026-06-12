---
title: "Cannot use xrdp"
date: 2010-07-29
forum: General Help
---

### Post by erezz on 2010-07-29
Hi,

I'm trying to start the xrdp service:

[erez@erez-lx:~]$ sudo /etc/init.d/xrdp restart
Stopping xrdp: sesman xrdp.
Starting xrdp: It looks like xrdp is allready running,
if not delete the xrdp.pid file and try again
xrdp sesman.

I could not find the xrdp.pid file. I also tried to remove the xrdp package and reinstall it. Nothing works. Can anyone help?

Thanks,
Erez

---

### Post by erezz on 2010-08-03
Anyone?

---

### Post by P4man on 2010-08-03
Have a look here:
[https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/339032](https://bugs.launchpad.net/ubuntu/+source/xrdp/+bug/339032)

maybe that helps. Also shows where the PID file ought to be (/var/run/xrdp).

---

### Post by erezz on 2010-08-03
Thanks!

---

