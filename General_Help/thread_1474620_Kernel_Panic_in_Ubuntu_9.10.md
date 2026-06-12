---
title: "Kernel Panic in Ubuntu 9.10"
date: 2010-05-06
forum: General Help
---

### Post by changlinn on 2010-05-06
Having a really odd problem. I get the usual kernel panic that kills the system, everything is unresponsive, if the screen is in screensaver it won't come out just the usual caps and numlock key flashing, if I have a tty open there is nothing dumped to screen. 
I have seen this happen when transferring large amounts of files to a USB NTFS formatted drive, but I have isolated that and made it occur when just doing a dist-upgrade.
I am pretty sure it is hardware but I am not sure where as this is the second build (last was 7.10 so I thought I would rebuild).
dmesg and syslog don't show anything obvious beyond the below in syslog shortly before the panic.
May  6 21:52:58 computar kernel: [   79.296570] ondemand governor failed, too long transition latency of HW, fallback to performance governor
I tried disabling ondemand by simply doing the below to no avail.
```
/etc/init.d/ondemand stop
```

I tried running 

```
stress --cpu 4 --io 4 --vm-bytes 128M --hdd 4 --timeout 120s
```

And I get an odd crash without the usual telltale kernal panic flashing keyboard lights. Ran memtest86+ for a little over 48hours with no issue, but the system itself won't run for 48hours under next to no load. I have run hard drive diags, and cpu stress tests from a live cd with no issue.
At a loss as to where to go from here, I am thinking video card but I want to be sure.

stand corrected, running the stress just now worked (twice), I may have been doing and apt-get install in another tty

```
stress --cpu 4 --io 4 --vm-bytes 128M --hdd 4 --timeout 120s
stress: info: [2326] dispatching hogs: 4 cpu, 4 io, 0 vm, 4 hdd
stress: info: [2326] successful run completed in 122s
```

---

### Post by changlinn on 2010-05-06
Yikes posted ten hours ago and already on page 19.

I think this forum needs to be split up to reduce the noise.

---

### Post by changlinn on 2010-05-10
Bump?

---

