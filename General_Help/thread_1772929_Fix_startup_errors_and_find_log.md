---
title: "Fix startup errors and find log"
date: 2011-06-01
forum: General Help
---

### Post by kabeza on 2011-06-01
Hi
I have Ubuntu 10.10 and am having some startup errors.

- I see some text before plymouth which can't read because of the speed which shows/hides.

- Plymouth loads in text mode only, showing Ubuntu 10.10 and not as it should. I guess this is due to my GF8400gs board and known problems between nvidia/ubuntu.

Finally, the x server (graphic mode) starts correctly and gdm shows fine, etc. but I'd like to try to fix these problems I'm having, to avoid future ones (in case I decide to upgrade, etc.)

**Is there any startup log file I could see? Something to fix plymouth resolution, etc.?**

Thanks,

---

### Post by ruffEdgz on 2011-06-01
If you didn't change anything in your rsyslog configurations, you should be able to grep your /var/log/ directory for 'plymouth':
```

sudo grep -ir plymouth /var/log/*

```
This should be able to give you the information you need for moving forward with this. I was able to do this in my logs directory and found a few files that had it on hand.

Cheers!

---

### Post by kabeza on 2011-06-02
Thanks ruffEdgz
I've executed the command, and found these suspicious lines, but can't take a decision about what I should do to fix these errors... can you deduct anything?

> /var/log/bootstrap.log:Selecting previously deselected package libplymouth2.
/var/log/bootstrap.log:Unpacking libplymouth2 (from .../libplymouth2_0.8.2-2ubuntu5_i386.deb) ...
/var/log/bootstrap.log:insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-splash'
/var/log/bootstrap.log:insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-splash'
/var/log/bootstrap.log:insserv: warning: script 'plymouth-log' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-log'
/var/log/bootstrap.log:insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-log'
/var/log/bootstrap.log:insserv: warning: script 'plymouth' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth'
/var/log/bootstrap.log:insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth'
/var/log/bootstrap.log:insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
/var/log/bootstrap.log:insserv: Default-Start undefined, assuming empty start runlevel(s) for script `plymouth-stop'
/var/log/bootstrap.log:insserv: Default-Stop  undefined, assuming empty stop  runlevel(s) for script `plymouth-stop'
/var/log/bootstrap.log:Selecting previously deselected package plymouth.
/var/log/bootstrap.log:Unpacking plymouth (from .../plymouth_0.8.2-2ubuntu5_i386.deb) ...
/var/log/bootstrap.log:Setting up libplymouth2 (0.8.2-2ubuntu5) ...
/var/log/bootstrap.log:Setting up plymouth (0.8.2-2ubuntu5) ...
/var/log/daemon.log:May 31 07:51:18 ubuntukikebeza init: plymouth-stop pre-start process (1896) terminated with status 1
/var/log/daemon.log:Jun  1 07:59:51 ubuntukikebeza init: plymouth-stop pre-start process (1881) terminated with status 1
/var/log/daemon.log:Jun  2 07:48:15 ubuntukikebeza init: plymouth-stop pre-start process (1901) terminated with status 1
/var/log/daemon.log.1:May 24 07:37:43 ubuntukikebeza init: plymouth-stop pre-start process (1892) terminated with status 1
/var/log/daemon.log.1:May 26 07:54:33 ubuntukikebeza init: plymouth-stop pre-start process (1858) terminated with status 1
/var/log/daemon.log.1:May 27 07:56:42 ubuntukikebeza init: plymouth-stop pre-start process (1889) terminated with status 1
/var/log/daemon.log.1:May 27 07:58:24 ubuntukikebeza init: plymouth-stop pre-start process (1939) terminated with status 1
/var/log/daemon.log.1:May 30 07:55:08 ubuntukikebeza init: plymouth-stop pre-start process (1879) terminated with status 1
/var/log/installer/syslog:Jan 24 09:03:13 ubuntu init: plymouth-stop pre-start process (2606) terminated with status 1
/var/log/syslog.1:Jun  2 07:48:15 ubuntukikebeza init: plymouth-stop pre-start process (1901) terminated with status 1


Thanks again,

---

