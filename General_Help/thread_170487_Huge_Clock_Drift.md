---
title: "Huge Clock Drift"
date: 2006-05-04
forum: General Help
---

### Post by embsupafly on 2006-05-04
Let me start off by saying that I have already been through this post, doesn't seem to help:

[http://www.ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed](http://www.ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed)

I have a machine running an Athlon 64, and the clock drift is about 300% (1 minute elapsed shows as 3 minutes). The hardware clock is fine, but the system clock is the one with a problem.

NTP works at bootup, and I can run ntpdate ntp.ubuntulinux.org to fix the system clock, and I get the current time, but then it starts up with the drift again.

I was thinking about setting a cron job to run every minute for ntpupdate, but thats going to waste alot of the bandwidth of the ntp server.

Any ideas?

---

### Post by embsupafly on 2006-05-04
Running adjtimex suggests a tick rate of 5092, however, if I try to set it to that, it complains that the lowest value it can accept for the kernel I am using is 9000.

Since the hardware clock is good, couldn't I just run this as a cron every minute:

hwclock --hctosys

???

---

### Post by embsupafly on 2006-05-05
Can anyone answer this question... please?

---

