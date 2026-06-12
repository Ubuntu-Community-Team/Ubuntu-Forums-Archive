---
title: "Ubuntu Desktop 64-bit sporadically closes all programs and shows logon"
date: 2012-06-06
forum: General Help
---

### Post by Paideuma on 2012-06-06
While using my workstation the logon screen will display without warning and at unpredictable intervals. When I sign back in to my machine, I find that all of the programs that were running are either closed or no longer visible. The amount of Memory used, however, is higher. It's as if the Memory that was being used before the "crash" remains in use. This "crash" is not preceded by a noticeable system slowdown, and I am using only a fraction of my system's resources.

I put crash in quotes because I'm not sure if this is a crash or not. There is no crash dialog that I can see before or after the logon screen displays.

I'd like to fix this problem or, at the very least, file a useful bug report.

How do I start diagnosing the cause? I suspect it will require examining some kind of a log. What log should I look for? I see nothing obvious in the syslog, but I'm not a developer. I imagine it is also possible that I need to enable some kind of special logging daemon to capture more information than is captured in a standard log.

My system specs:
* Dual boot Windows 7 + Ubuntu 12.04 (precise) 64-bit
* Kernal Linux 3.2.0-24-generic
* GNOME 3.4.1
* Memory: 7.8 GiB
* Processor: Intel Xenon CPU E5405 @ 2.00GHz x 4
* Available disk space: 113.8 GiB

---

### Post by Paideuma on 2012-06-06
OK, it just did it again, and this time I immediately looked at the syslog. Here's what I am seeing.

```
Jun  6 15:56:01 nblanchet-Ubuntu kernel: [ 2192.122073] NVRM: Xid (0000:01:00): 6, PE0001 
Jun  6 15:56:01 nblanchet-Ubuntu gnome-session[1785]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Jun  6 15:56:01 nblanchet-Ubuntu acpid: client 1012[0:0] has disconnected
Jun  6 15:56:01 nblanchet-Ubuntu acpid: client 1012[0:0] has disconnected
Jun  6 15:56:01 nblanchet-Ubuntu acpid: client connected from 12593[0:0]
Jun  6 15:56:01 nblanchet-Ubuntu acpid: 1 client rule loaded
Jun  6 15:56:01 nblanchet-Ubuntu acpid: client connected from 12593[0:0]
Jun  6 15:56:01 nblanchet-Ubuntu acpid: 1 client rule loaded
Jun  6 15:56:02 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 12737 of process 12737 (n/a) owned by '104' high priority at nice level -11.
Jun  6 15:56:02 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 1 threads of 1 processes of 1 users.
Jun  6 15:56:02 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 12743 of process 12737 (n/a) owned by '104' RT at priority 5.
Jun  6 15:56:02 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 2 threads of 1 processes of 1 users.
Jun  6 15:56:02 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 12744 of process 12737 (n/a) owned by '104' RT at priority 5.
Jun  6 15:56:02 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 3 threads of 1 processes of 1 users.
Jun  6 15:56:02 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 12747 of process 12747 (n/a) owned by '104' high priority at nice level -11.
Jun  6 15:56:02 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 4 threads of 2 processes of 1 users.
Jun  6 15:56:02 nblanchet-Ubuntu pulseaudio[12747]: [pulseaudio] pid.c: Daemon already running.
Jun  6 15:56:08 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 12872 of process 12872 (n/a) owned by '1000' high priority at nice level -11.
Jun  6 15:56:08 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 4 threads of 2 processes of 2 users.
Jun  6 15:56:09 nblanchet-Ubuntu pulseaudio[12872]: [pulseaudio] pid.c: Stale PID file, overwriting.
Jun  6 15:56:09 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 12905 of process 12872 (n/a) owned by '1000' RT at priority 5.
Jun  6 15:56:09 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 5 threads of 2 processes of 2 users.
Jun  6 15:56:09 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 12908 of process 12872 (n/a) owned by '1000' RT at priority 5.
Jun  6 15:56:09 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 6 threads of 2 processes of 2 users.
```

The previous entry in the syslog is dated "Jun  6 15:27:26". The second line is showing a "Fatal IO error". Could that indicate something useful?

---

### Post by Paideuma on 2012-06-06
Aaaaand it just did it again. (Apparently, it doesn't like me investigating it.) Here's the relevant syslog excerpt.

```
Jun  6 16:08:02 nblanchet-Ubuntu kernel: [ 2913.946405] NVRM: Xid (0000:01:00): 6, PE0001 
Jun  6 16:08:03 nblanchet-Ubuntu kernel: [ 2914.101236] do_general_protection: 36 callbacks suppressed
Jun  6 16:08:03 nblanchet-Ubuntu kernel: [ 2914.101240] Xorg[12593] general protection ip:7f3ccd6a06a9 sp:7fff6999f370 error:0 in nvidia_drv.so[7f3ccd63f000+6e0000]
Jun  6 16:08:03 nblanchet-Ubuntu gnome-session[12794]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :1.#012
Jun  6 16:08:03 nblanchet-Ubuntu acpid: client 12593[0:0] has disconnected
Jun  6 16:08:03 nblanchet-Ubuntu acpid: client 12593[0:0] has disconnected
Jun  6 16:08:03 nblanchet-Ubuntu acpid: client connected from 13635[0:0]
Jun  6 16:08:03 nblanchet-Ubuntu acpid: 1 client rule loaded
Jun  6 16:08:03 nblanchet-Ubuntu acpid: client connected from 13635[0:0]
Jun  6 16:08:03 nblanchet-Ubuntu acpid: 1 client rule loaded
Jun  6 16:08:04 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 13750 of process 13750 (n/a) owned by '104' high priority at nice level -11.
Jun  6 16:08:04 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 1 threads of 1 processes of 1 users.
Jun  6 16:08:04 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 13755 of process 13750 (n/a) owned by '104' RT at priority 5.
Jun  6 16:08:04 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 2 threads of 1 processes of 1 users.
Jun  6 16:08:04 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 13756 of process 13750 (n/a) owned by '104' RT at priority 5.
Jun  6 16:08:04 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 3 threads of 1 processes of 1 users.
Jun  6 16:08:04 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 13760 of process 13760 (n/a) owned by '104' high priority at nice level -11.
Jun  6 16:08:04 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 4 threads of 2 processes of 1 users.
Jun  6 16:08:04 nblanchet-Ubuntu pulseaudio[13760]: [pulseaudio] pid.c: Daemon already running.
Jun  6 16:08:08 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 13884 of process 13884 (n/a) owned by '1000' high priority at nice level -11.
Jun  6 16:08:08 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 4 threads of 2 processes of 2 users.
Jun  6 16:08:08 nblanchet-Ubuntu pulseaudio[13884]: [pulseaudio] pid.c: Stale PID file, overwriting.
Jun  6 16:08:08 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 13906 of process 13884 (n/a) owned by '1000' RT at priority 5.
Jun  6 16:08:08 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 5 threads of 2 processes of 2 users.
Jun  6 16:08:09 nblanchet-Ubuntu rtkit-daemon[1651]: Successfully made thread 13907 of process 13884 (n/a) owned by '1000' RT at priority 5.
Jun  6 16:08:09 nblanchet-Ubuntu rtkit-daemon[1651]: Supervising 6 threads of 2 processes of 2 users.
```

It looks like that Fatal IO error is back, but so is the NVRM: Xid line.

---

