---
title: "Periodic CPU spikes after recent update"
date: 2010-03-07
forum: General Help
---

### Post by bomgd3 on 2010-03-07
Hey everyone,
I'm fairly new to Ubuntu and I'm experiencing a fairly serious, deal-breaking bug.  My overall experience with Linux has been almost completely positive, but I just started having something really weird come up.

I'm having periodic CPU spikes of about 50% on one of my cores, and it's interfering with lots of things.  Audio skips a lot, my mouse and keyboard skip, scrolling is jumpy, etc.  It happens once approximately every 2.5 seconds.  I haven't been able to isolate any single process--System Monitor's Processes tab doesn't show anything unusual, yet it clearly shows a process taking up 50% of a CPU at a highly periodic interval.

Could you guys help me figure out the culprit?  I recently did an auto-update, so I think maybe something got broken during the update.

I'm running Karmic on a Thinkpad T61 w/NVidia Quadro graphics.  I attached a screenshot of the CPU monitor.

---

### Post by flippo on 2010-03-07
I don't user system monitor, but if you run top (open a terminal and type top) then it will show you the process taking up the most cpu.  Once you know the process it should be much easier to debug.

---

### Post by bomgd3 on 2010-03-07
Thanks.  I tried top already, but it wasn't very insightful.  Something called events/1 is taking up 13%, but it is not doing so in a periodic way.

By the way, I noticed that my kernel was upgraded in yesterday's update.  It went from linux-generic 2.6.31.20.32 to 33...  maybe that is the issue?  In grub, I tried to boot into a second Ubuntu entry (I'm assuming a different kernel version?) and the CPU spiking remained, but was shifted to CPU2 instead of CPU1.  That's sort of strange and indicates to me that the kernel update is the culprit, somehow.

[edit] I also just had a full crash out of X back to the login screen.  Sound is still super-skippy.  Something fishy is going on here.  Can I somehow roll back to the last kernel version?  Or do you guys think something else is messing up my installation?

[another edit] One other strange thing I noticed is that my grub menu appeared.  Before, it would boot directly into Ubuntu, no questions asked.  Now, it gives me like 4 different Ubuntu options.  What the heck is going on here?

---

### Post by bomgd3 on 2010-03-07
Final update, in case anyone else has this issue.  I found an older thread that said to boot with the flags acpi=off and apm=off.  I did that, and my OS basically went into an infinite loop at login.  It would flash the "login" terminal message, but would never get to GDM.

After that, I deleted the flags to get things back to normal.  When I got back into Ubuntu, I found that the weird spikes stopped.  So I guess it was some strange power management freakout that needed a refresh.

---

