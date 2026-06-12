---
title: "Lastfmsubmitd.pid file in home directory not in /var/run/lastfm"
date: 2009-12-10
forum: General Help
---

### Post by bananabob on 2009-12-10
I have been getting the following error:

/etc/cron.daily/logrotate:
can't open pidfile: [Errno 2] No such file or directory: '/var/run/lastfm/lastfmsubmitd.pid'
error: error running postrotate script for /var/log/lastfm/lastfm.log
run-parts: /etc/cron.daily/logrotate exited with return code 1

I also get an error on bootup that the lastfmsubmitd.pid file is missing.

I have just found the missing pid file but not on /var/run/lastfm it is sitting in my home directory.

Is there anyone out there who can tell me how to get the pid file into the /var/run/lastfm directory?

I have Ubuntu Hardy 8.04.3 and am using lastfmsubmit 0.36-1 from the Synaptic package list.

Cheers
James

---

