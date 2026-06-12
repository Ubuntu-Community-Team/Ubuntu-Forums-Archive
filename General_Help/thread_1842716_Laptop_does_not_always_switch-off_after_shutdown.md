---
title: "Laptop does not always switch-off after shutdown"
date: 2011-09-12
forum: General Help
---

### Post by DeMus on 2011-09-12
Hi,

My Samsung R730 laptop with LinuxMint 11 Katya-64bits has a problem since recently. Sometimes, not always, it won't switch-off after shutdown.
I looked in the syslog file and found this during the time it should switch-off:

```
Sep  8 22:27:54 R-730-Linux nmbd[2053]: [2011/09/08 22:27:54.058874,  0] nmbd/nmbd.c:71(terminate)
Sep  8 22:27:54 R-730-Linux nmbd[2053]:   Got SIGTERM: going down...
Sep  8 22:27:54 R-730-Linux kernel: Kernel logging (proc) stopped.
Sep  8 22:27:54 R-730-Linux rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="825" x-info="http://www.rsyslog.com"] exiting on signal 15.
```

The picture is black at the time so I can't see what's happening, but the lights are still on so the computer did not switch-off.
Who knows some more about what could be the problem here?

---

### Post by DeMus on 2011-09-17
I sort of solved my problem by installing a new OS: LMDE in 64 bits Gnome version. Now, with all updates installed it shuts down and restarts very well.
I mark this thread solved although the real problem has not been solved.

Well, also LMDE has the same problem as does Ubuntu 11.04. So something is definitive wrong here.

---

