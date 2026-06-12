---
title: "gma500 suspend after hibernate"
date: 2010-01-18
forum: General Help
---

### Post by dragilla on 2010-01-18
Hello,
I have ubuntu server + xfce4 installed on my Vaio P92.
Add 2.6.32.3 custom built kernel and you have a picture of what'm working with.

My problem is that my netbook will only suspend after I hibernate and restore. If I try to suspend/restore after a regular reboot I get a X hang (i can kill X with alt-sysrq-k).

In the /var/log/pm-suspend i get:
```

/usr/lib/pm-utils/sleep.d/99video resume suspend: Function not supported
success.

```

I might add it worked before (with this kernel and psb drivers). I must've changed something, but no idea what could it be. I played with alsa a bit but can't seem to connect the problem to it.

Let me know if you have an idea or maybe should I provide more info.

cheerss,
-- 
LS

---

### Post by MartinChir on 2010-01-22
I have a similar problem on a Dell Mini 10/GMA 500, after the monitor turns off it doesn't come back, stays black. Not sure if the system has tried to suspend or just the screen has turned off.

---

### Post by inadeqite on 2010-01-28
> **dragilla said:**
> Hello,
I have ubuntu server + xfce4 installed on my Vaio P92.
Add 2.6.32.3 custom built kernel and you have a picture of what'm working with.

My problem is that my netbook will only suspend after I hibernate and restore. If I try to suspend/restore after a regular reboot I get a X hang (i can kill X with alt-sysrq-k).

In the /var/log/pm-suspend i get:
```

/usr/lib/pm-utils/sleep.d/99video resume suspend: Function not supported
success.

```I might add it worked before (with this kernel and psb drivers). I must've changed something, but no idea what could it be. I played with alsa a bit but can't seem to connect the problem to it.

Let me know if you have an idea or maybe should I provide more info.

cheerss,
-- 
LS

I have same problem. My Dell mini can't resume after suspend (black screen, but backlight and hdd work).

---

### Post by blur xc on 2010-08-07
> **inadeqite said:**
> I have same problem. My Dell mini can't resume after suspend (black screen, but backlight and hdd work).

Me too- after an upgrade to 10.04.

I hit ctrl-alt-f1 and then blindly logged in and rebooted from the command line...  so everything is working, it's like the x-server won't fire back up...

Thanks,
BM

---

### Post by blur xc on 2010-08-09
I found out that 10.04 has a newer xserver version that doesn't work so great with the poulsbo gma500 driver, and in essence, the x-server crashes and won't resume when you try to resume from suspend.

I found a fix in the gma500 megathread but haven't figured out how ot implement it...  still working on that one.

BM

---

### Post by cr0m on 2010-11-07
I'm very interested in a fix for this issue. The GMA500 mega-thread is so long it's difficult to wade through it for a newbie.

I actually implemented the s2ram fix documented here:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Tweaks)

So I'm able to suspend the machine, just not by using the suspend button on my netbook. Or by closing the netbook, which more of a bummer.

---

