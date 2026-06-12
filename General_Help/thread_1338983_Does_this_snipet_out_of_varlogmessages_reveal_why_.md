---
title: "Does this snipet out of /var/log/messages reveal why my system crashed?"
date: 2009-11-27
forum: General Help
---

### Post by second.exodous on 2009-11-27
I'm trying to find out why my system keeps crashing and this time I looked at my clock exactly when it crashed and this is a snippet is from that time period:
```

Nov 26 23:51:40 user-desktop kernel: [   28.588155] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Nov 26 23:51:40 user-desktop kernel: [   28.588271] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
Nov 26 23:52:04 user-desktop kernel: [   36.000027] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Nov 26 23:52:28 user-desktop kernel: [   59.995731] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Nov 26 23:53:28 user-desktop kernel: [  119.995802] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Nov 26 23:54:48 user-desktop kernel: [  199.995832] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Nov 26 23:56:25 user-desktop kernel: [  297.542103] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Nov 26 23:56:30 user-desktop kernel: [  302.650257] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Nov 26 23:58:28 user-desktop kernel: [  419.995780] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Nov 27 00:00:28 user-desktop kernel: [  539.995752] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83
Nov 27 00:01:43 user-desktop kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Nov 27 00:01:43 user-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="931" x-info="http://www.rsyslog.com"] (re)start
Nov 27 00:01:43 user-desktop rsyslogd: rsyslogd's groupid changed to 102
Nov 27 00:01:43 user-desktop rsyslogd: rsyslogd's userid changed to 101
Nov 27 00:01:43 user-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 27 00:01:43 user-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Nov 27 00:01:43 user-desktop kernel: [    0.000000] Linux version 2.6.31-15-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 (Ubuntu 2.6.31-15.50-generic)
Nov 27 00:01:43 user-desktop kernel: [    0.000000] KERNEL supported cpus:
Nov 27 00:01:43 user-desktop kernel: [    0.000000]   Intel GenuineIntel
Nov 27 00:01:43 user-desktop kernel: [    0.000000]   AMD AuthenticAMD
Nov 27 00:01:43 user-desktop kernel: [    0.000000]   NSC Geode by NSC
Nov 27 00:01:43 user-desktop kernel: [    0.000000]   Cyrix CyrixInstead
Nov 27 00:01:43 user-desktop kernel: [    0.000000]   Centaur CentaurHauls
Nov 27 00:01:43 user-desktop kernel: [    0.000000]   Transmeta GenuineTMx86
Nov 27 00:01:43 user-desktop kernel: [    0.000000]   Transmeta TransmetaCPU
Nov 27 00:01:43 user-desktop kernel: [    0.000000]   UMC UMC UMC UMC
Nov 27 00:01:43 user-desktop kernel: [    0.000000] BIOS-provided physical RAM map:
```
None of this makes sense, should I be looking somewhere else to find a crash log?  Any help would be appreciated.

---

### Post by diesch on 2009-11-27
The crash happend after00:00:28. At 00:01:43 the system was restarted so log entries after this aren't connect to the crash.

The  [FONT=monospace]"[/FONT]*===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 83*" lines are spread over a period of more than 8 minutes so I don't think they are connected to the crash.

Everything else occured at least about 4 minutes before the the crash so I don't think it's  connected to the crash.

---

### Post by dtschmitz on 2009-11-28
I am troubleshooting a situation similar to yours, with the same verbiage for rsyslog.

Mine is an HP dv2000z AMD Turion64x2 which fails to boot with exception of kernel option 'nosmp' or 'maxcpus=1'.

If I do boot with either of those kernel boot options, I am left with just one core running in 2.6.31-15 Generic SMP on Ubuntu 9.10.  There are no bios options that one can set on this machine--using Phoenix BIOS F.22

Otherwise, the machine does a hard stop and as such doesn't have a chance to write out anything in the log for the error encountered.

As my kernel shows WatchDog hooks are compiled in, I've installed WatchDog and have given a kernel option of:

debug panic=10 loglevel=7 nmi_watchdog=1 

in the hopes of catching additional info in the log.

So, far, I am not making sense of this.  
My heart goes out to you! :)

---

### Post by second.exodous on 2009-12-07
I thought I'd update this thread.  It turns out that it was my computer, I've always thought my memory was set up incorrectly and I did a google search

```
M4A78T-E 996601
```

M4A78T-E because that's my Asus motherboard and 996601 because that's the part number of my Mushkin memory.  The second result told me how to set up my memory correctly.  When I built my computer both the motherboard and memory were new and no one had set it up correctly.

I did some more research and lock-ups like I was experiencing are often the cause of incorrectly configured memory.  So if you built your own system and have lock ups look into that with a simple Google search.

I've been running my system like this for a little a week or so and hasn't gone down once where before it was a few times a day.  I really hope this helps someone, 8.10 and 9.04 it locked up once a week but 9.10 was a little more sensitive.

---

### Post by Kevbert on 2009-12-07
To mark thread as solved just select it from the pull-down menu 'Thread Tools' on the right-hand side.

---

### Post by second.exodous on 2009-12-07
Ah, ok, found it.  A little different from other forums.

---

