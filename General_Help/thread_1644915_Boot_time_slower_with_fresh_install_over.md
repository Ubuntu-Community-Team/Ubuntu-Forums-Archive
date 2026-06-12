---
title: "Boot time slower with fresh install over"
date: 2010-12-13
forum: General Help
---

### Post by at100plus on 2010-12-13
I was getting amazing boot time when I had Ubuntu installed as Wubi (inside Windows).

I saw 13 - 15 second complete boot from pressing power button to useable desktop!  I was so happy with that I thought it would be even better with a fresh install (plus I'm more than ready to have Mr. Gates out of my life for good!).

I have a Dell XPSM1530 with a 68G Solid State Drive, 2GHZ processor Dual Core and 4G Ram (32bit).

I went through the startup and boot managers, tweaked out as much as I could find, set for best performance, checked bios settings for anthing that might be slowing it down, didn't find anything.

I'm so disappointed, my boot time is closer to 40 or 50 seconds now.

I think I read something that wubi kinda hibernates rather than complete shut down.  Is that the reason?

---

### Post by oldfred on 2010-12-14
My 4GB & standard hard drives with lots of partitions to mount (which slows it somewhat) takes about 50-60sec. You should be a lot faster with SSD drive.

Is Ubuntu in a smallish partition 10-20GB in the SSD with /home or data mounted on standard drives? 

Have you checked log files to see what is taking so long? System, Administration log file view. Look for long times between transactions or repeated tries at loading a driver and then a timeout.

---

### Post by at100plus on 2010-12-14
I installed Ubuntu on a fresh format of the entire drive with no partitions, then I installed Virtual Box with a 10 GB virtual hard disk and installed Win7 on that.

I'll check the logs.

---

