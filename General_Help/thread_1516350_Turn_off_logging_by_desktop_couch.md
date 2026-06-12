---
title: "Turn off logging by desktop couch"
date: 2010-06-23
forum: General Help
---

### Post by r-senior on 2010-06-23
Desktop couchdb builds up a pair of log files in:

~/.cache/desktop-couchdb.log.1
~/.cache/desktop-couchdb.stdout.1

It appears they then get rotated to *.2 and *.3 before disappearing.

In my case, having uninstalled Ubuntu One, I think the desktop couch DB is only there supporting Gwibber. Both log files seem to be HTTP access logs - referring to HEAD and GET - not much value really.

If the machine is up for several days, these logs get quite large. I think they were up to a combined 700MB after 12 days uptime before I rebooted today.

There's a settings file /etc/couchdb/local.ini but the log level therein only seems to affect the log under /var/log/couchdb.

Anyone know how to stop this logging under ~/.cache?

---

### Post by r-senior on 2010-07-16
Well I never found a solution and desktopcouch had to go (and take Gwibber with it) when the disk usage went over 1.5GB. Not a lot on modern, capacious disks, but my desktop is using 2 x 8GB drives and 1.5GB is a lot to take out of /home for what it is.

Pino is the replacement and does the job (look forward to the combined timeline on multiple accounts).

Is this indefinite/unreasonable growth from desktopcouch/Gwibber a bug? Would you report it?

---

