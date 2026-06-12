---
title: "keep losing audio randomly while -- pulseaudio suspected"
date: 2010-05-19
forum: General Help
---

### Post by uiberto on 2010-05-19
Hi,

I keep having problems where my audio cuts out in the middle of listening to anything (Flash, VLC, etc). It's becoming very frustrating.

I'm running a realtime kernel so I'm wondering if that has something to do with it. Others have reported this problem: [https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/367671](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+bug/367671)

Any ideas are appreciated. Thanks.

uiberto


/var/log/syslog
May 18 21:02:58 localhost rtkit-daemon[4743]: Failed to make ourselves RT: Invalid argument
May 18 21:02:58 localhost rtkit-daemon[4743]: last message repeated 10 times
May 18 21:02:58 localhost pulseaudio[7513]: pid.c: Stale PID file, overwriting.
May 18 21:02:58 localhost rtkit-daemon[4743]: Failed to make ourselves RT: Invalid argument
May 18 21:02:58 localhost rtkit-daemon[4743]: last message repeated 10 times
May 18 21:02:58 localhost pulseaudio[7519]: pid.c: Daemon already running.

uname -a
Linux localhost 2.6.31-10-rt #153-Ubuntu SMP PREEMPT RT Tue Jan 12 11:01:03 UTC 2010 x86_64 GNU/Linux

---

### Post by JayRobert on 2010-05-19
Yes, I have had this problem since installing ubuntu studio 10.04.  I did not have this problem with studio karmic 9.10.  I have tried six kernels, same issue.  Also flash only works on some video files (no video or sound on about half of youtube's postings).

The kernels I have tried include 2.6.31-10-rt (the same kernel studio karmic used); 2.6.31-12-realtime (from Alessio Bogani's ppa); 2.6.33-1-realtime (ditto); 2.6.32-21-preempt (on the iso file); 2.6.32-22-preempt (the upgrade); and 2.6.32-22-lowlatency.  I have also tried what little I know to figure out pulseaudio.

I haven't had this problem using audacity or other purely audio packages - it seems to be a problem with the flash players that are available.  I suspect that what's available just doesn't work as well as Java, which has been deprecated in 10.04.

---

### Post by nicolach on 2010-06-18
Had this exact same problem, on a fresh 64-bit install of 10.04. No sound when playing videos of any kind, but rhythmbox played soundfiles w/o a hitch.
So it had to be a backend problem. It could be either gstreamer or pulseaudio. so I checked Pulseaudio device chooser & lo and behold, it had chosen the wrong audio output. problem solved. hope this helps somebody.

---

