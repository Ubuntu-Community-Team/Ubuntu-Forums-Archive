---
title: "Ubuntu 10.04.3 hangs while booting"
date: 2012-01-12
forum: General Help
---

### Post by Aster.Orthrinos on 2012-01-12
Hi everyone! I have Ubuntu 10.04.3 without any updates suggested by system but with some aditional installed packages added manualy after install. One day it started to hang while booting. Visualy it is when purple screen appears with white Ubuntu logo in center and dots lights up bellow. I tried to restore grub but this did not helped. 

Then, today I launched notebook approximetly in 8:30 and went out. I came back about in 12:30 and made restart to see logs through Boot Repair Live CD. I looked what is written in var/log/syslog and look what I founded (I place only part):

```
08:30:05 ubuntu kernel: [   28.234387] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Jan 12 08:30:05 ubuntu kernel: [   28.234461] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Jan 12 08:30:05 ubuntu kernel: [   28.235113] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Jan 12 08:30:05 ubuntu init: apport pre-start process (627) terminated with status 1
Jan 12 08:30:05 ubuntu cron[632]: (CRON) INFO (pidfile fd = 3)
Jan 12 08:30:05 ubuntu acpid: starting up with netlink and the input layer
Jan 12 08:30:05 ubuntu anacron[647]: Anacron 2.3 started on 2012-01-12
Jan 12 08:30:05 ubuntu cron[649]: (CRON) STARTUP (fork ok)
Jan 12 08:30:05 ubuntu cron[649]: (CRON) INFO (Running @reboot jobs)
Jan 12 08:30:05 ubuntu init: apport post-stop process (644) terminated with status 1
Jan 12 08:30:05 ubuntu acpid: 36 rules loaded
Jan 12 08:30:05 ubuntu acpid: waiting for events: event logging is off
Jan 12 08:30:05 ubuntu anacron[647]: Normal exit (0 jobs run)
Jan 12 08:30:05 ubuntu kernel: [   28.578775] ppdev: user-space parallel port driver
Jan 12 08:30:06 ubuntu kernel: [   28.796764] intel8x0_measure_ac97_clock: measured 55235 usecs (2661 samples)
Jan 12 08:30:06 ubuntu kernel: [   28.796770] intel8x0: clocking to 48000
Jan 12 08:30:06 ubuntu anacron[782]: Anacron 2.3 started on 2012-01-12
Jan 12 08:30:06 ubuntu anacron[782]: Normal exit (0 jobs run)
Jan 12 09:17:01 ubuntu CRON[810]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 10:17:01 ubuntu CRON[815]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 11:17:01 ubuntu CRON[820]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 12:17:01 ubuntu CRON[825]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 12 12:49:35 ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jan 12 12:49:35 ubuntu rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="500" x-info="http://www.rsyslog.com"] (re)start
Jan 12 12:49:35 ubuntu rsyslogd: rsyslogd's groupid changed to 103
Jan 12 12:49:35 ubuntu rsyslogd: rsyslogd's userid changed to 101
Jan 12 12:49:35 ubuntu rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jan 12 12:49:35 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 12 12:49:35 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 12 12:49:35 ubuntu kernel: [    0.000000] Linux version 2.6.32-33-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 (Ubuntu 2.6.32-33.70-generic 2.6.32.41+drm33.18)
```Please help me to solve this proplem.

---

