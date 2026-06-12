---
title: "Karmic keyboard/mouse lag on disk activity"
date: 2010-03-06
forum: General Help
---

### Post by arvana on 2010-03-06
Hi all, I recently switched to 64-bit Karmic after installing extra memory.  I have everything working fine, but I am experiencing an annoying lag in keyboard and mouse response whenever any of the CPU cores briefly jumps to 100% usage, which tends to happen every 10 to 15 seconds, usually caused by firefox.

I'll be typing or scrolling, and there is fairly regularly a hesitation of a second or two in which nothing happens on-screen, and then everything catches up again, ie the keyboard buffer empties to screen or the page scrolls a lot.

I've tried changing the Nvidia driver and the disk iosched elevator, which were the only ideas I could find when searching on this issue.

It seems to me that (a) the CPU usage shouldn't be jumping up like that, and (b) even if it does, it shouldn't affect keyboard an mouse activity to such an extent.  This only started happening after switching from 32-bit to 64-bit Karmic.

If anybody can give me any suggestions of other things to try, I would be very grateful!

SYSTEM SPECS
Intel Q6600 2.4GHz quad-core CPU
Gigabyte EP45-UD3L motherboard (P45 chipset)
6 GB memory
Disk space: 2x 250GB drives + 1500GB RAID5
Ubuntu 9.10 64-bit
Linux 2.5.31-20 kernel

---

### Post by arvana on 2010-03-08
Bump.

---

### Post by hvbakel on 2010-03-08
I've experienced similar annoying lags in mouse responsiveness under medium to high cpu/disk activity, for example when opening large pdf files. What worked for me was to enable the NEW_FAIR_SLEEPERS scheduler feature (disabled by default in karmic) and to increase priority of the X server.

To enable fair sleepers you can add the following line to /etc/rc.local

```
echo NEW_FAIR_SLEEPERS > /sys/kernel/debug/sched_features
```

To increase the priority of the X server, you can run the following in a terminal:

```
sudo renice -10 `pidof X`
```

Setting X to run at a higher priority fixed the input lag for me, while enabling fair sleepers made the system much more responsive under high IO load. Though this fixed my problems, I'd love to find a more structural solution...

---

### Post by arvana on 2010-03-14
Thank you, hvbakel --

I tried your suggestions, and they definitely improve system response.  However I am still experiencing the same input lag.  It definitely seems to be related to Firefox creating CPU peaks every 10-15 seconds; I have tried disabling all Firefox extensions, disabling smooth scrolling, and renicing X to -20.  Still no good.

The simple answer is to switch to Chrome as a workaround, but it still doesn't solve the underlying problem: CPU peaks cause severe I/O latency.  I'm on a very fast machine, so this shouldn't be happening, and never did on any 32-bit version of Ubuntu.

Any other ideas / suggestions?

---

### Post by hvbakel on 2010-03-14
Sounds like something is wrong in your firefox profile. You could try moving or deleting (after making a backup of your bookmarks etc) the ~/.mozilla/firefox folder. When you start firefox it will generate a new profile automatically.

Alternatively, you could update to the latest firefox version (3.6) using the firefox-stable ppa at [https://launchpad.net/~mozillateam/+archive/firefox-stable/](https://launchpad.net/~mozillateam/+archive/firefox-stable/)

---

### Post by dcstar on 2010-03-14
> **hvbakel said:**
> Sounds like something is wrong in your firefox profile.
.......

Or it could be a bad block on the hard disk that is causing many retries each time it is accessed.

---

### Post by arvana on 2010-03-15
Firefox profile was the problem -- why didn't I think of that?  Thanks very much for the help!!

---

### Post by amulet on 2010-10-08
Just for the record, Firefox was dragging my computer performance down real badly. I followed advice from hvbakel re deleting mozilla/firefox folder and restarting Firefox (after backing up bookmarks) and it has worked like a dream.
Thank you hvbakel

---

