---
title: "clock keeps losing sync"
date: 2009-07-03
forum: General Help
---

### Post by sjv on 2009-07-03
Ever since upgrading to Jaunty, my clock has been getting way out of sync. NTP is started, and I have tried restarting it. I have tried switching time servers as well. I just reset the time to match(or close to it) this morning at 6:45, and now 3 hours later it's about 2-3 minutes ahead. Yesterday it managed to gain 16 minutes. This has never been a problem on my machine. It happened immediately after the upgrade. 

I tried the few things that were suggested in this thread:
[http://ubuntuforums.org/showthread.php?t=1167311](http://ubuntuforums.org/showthread.php?t=1167311)

but nothing did anything. Any thoughts?

Here's what I pulled from my syslog after a restart of ntpd:

```

Jul  3 09:51:34 dev1 ntpd[6617]: ntpd exiting on signal 15
Jul  3 09:51:36 dev1 ntpd[7109]: ntpd 4.2.4p4@1.1520-o Wed May 13 21:05:42 UTC 2009 (1)
Jul  3 09:51:36 dev1 ntpd[7110]: precision = 4000.000 usec
Jul  3 09:51:36 dev1 ntpd[7110]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Jul  3 09:51:36 dev1 ntpd[7110]: Listening on interface #1 wildcard, ::#123 Disabled
Jul  3 09:51:36 dev1 ntpd[7110]: Listening on interface #2 lo, ::1#123 Enabled
Jul  3 09:51:36 dev1 ntpd[7110]: Listening on interface #3 eth0, fe80::204:5aff:fe4a:a0d6#123 Enabled
Jul  3 09:51:36 dev1 ntpd[7110]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Jul  3 09:51:36 dev1 ntpd[7110]: Listening on interface #5 eth0, 192.168.1.93#123 Enabled
Jul  3 09:51:36 dev1 ntpd[7110]: kernel time sync status 0040
Jul  3 09:51:36 dev1 ntpd[7110]: frequency initialized 3.549 PPM from /var/lib/ntp/ntp.drift

```

---

### Post by michy99 on 2009-07-03
Try replacing the bios battery.

---

### Post by DeMus on 2009-07-03
> **michy99 said:**
> Try replacing the bios battery.

My experience with bad batteries is that time is running slow, not fast.


I just noticed I had set my time manual and even after a long time it is still running in sync. Now I switched to a ntp server. Let's see how this goes.

You did not fool around with your computer, overclocking or things like that?

---

### Post by sjv on 2009-07-03
I'll try replacing the battery. Same as DeMus said though. I have never experienced a bad battery causing the time to jump forward, it has always been the case that it loses time. The machine is always on though, so I would expect NTP to be keeping it synced up anyways.

---

