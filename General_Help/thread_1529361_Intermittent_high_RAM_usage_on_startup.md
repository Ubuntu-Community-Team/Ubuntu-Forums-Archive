---
title: "Intermittent high RAM usage on startup"
date: 2010-07-12
forum: General Help
---

### Post by Helios747 on 2010-07-12
Hello,

I use an Ubuntu 10.04 minimal install with only the packages I want, I like to keep things pretty slim.

On bootup, when I execute "startx", everything starts to load, this is fine. However, just off of a cold boot with only my startup apps running, conky shows around 450mb of RAM usage. It usually is only around 150 - 175.


Sometimes when I boot my computer Conky shows the normal RAM usage in the 150mb range, sometimes it's in the 450mb range.

My startup apps when I start X is openbox, tint2, wicd-gtk, feh (for wallpaper), and conky.

I open up htop when conky reports the weird RAM usage. htop also shows the weird RAM usage but I can't seem to find the memory hogging app.

Is this a kernel issue? I'm using the vanilla Ubuntu 10.04 kernel. Will recompiling from kernel.org fix this?

---

### Post by dino99 on 2010-07-12
you need to know which process is eating the ram: you can use system monitor to have more details

when you have found the probable faulty package, reconfigure it (them)

sudo dpkg-reconfigure yourpackage

some usefull errors can be logged too (xsession-errors, system admin logviewer)

---

### Post by Helios747 on 2010-07-12
I will try this when my RAM usage goes funny again and post what's going on.

Right now it's playing nice, thank you.

---

### Post by Helios747 on 2010-07-12
Okay, booting up today showed the weird RAM usage. I fired up gnome system monitor and sorted by apps using the most RAM but couldn't find anything that was causing the RAM usage to shoot up like that.

---

### Post by robert shearer on 2010-07-12
Symptoms = Occasionally on boot memory use is high and stays high.

Notes, look for this pattern... 
1) it usually happens after the machine has been shutdown from a session where **updates** were done. 
i.e. next boot after updates shows higher ram usage.

2) if you allow it to boot then immediately **reboot** the ram usage is always returned to normal.

Sounds like the system is being re-profiled for 'ureadahead'.

[http://ohioloco.ubuntuforums.org/showthread.php?t=1434502](http://ohioloco.ubuntuforums.org/showthread.php?t=1434502)

This high ram not being released was a glitch in  Lucid alphas and seems to be present again in Maverick.

Can't say I see it at all in current Lucid installs but ureadahead may impact low resource systems more.

There are plenty of threads on ureadahead, not saying that this is your problem but sounds close enough.

I am sure wiser minds can chip in and explain more (or correct my assumptions :D)

---

### Post by Helios747 on 2010-07-12
Hmm. You're right. It happens when I install stuff.

I assume this is a known bug and is being worked on?

Until then if the high RAM bugs me just reboot?

---

### Post by dcstar on 2010-07-14
> **robert shearer said:**
> Symptoms = Occasionally on boot memory use is high and stays high.

Notes, look for this pattern... 
1) it usually happens after the machine has been shutdown from a session where **updates** were done. 
i.e. next boot after updates shows higher ram usage.

2) if you allow it to boot then immediately **reboot** the ram usage is always returned to normal.
.......

Many things can happen on "boot up", cron jobs that are run daily, weekly or monthly may be started if the relevant time stamp is valid, on a subsequent reboot shortly after they won't run (because they already have been run).

---

### Post by robert shearer on 2010-07-14
> **dcstar said:**
> Many things can happen on "boot up", cron jobs that are run daily, weekly or monthly may be started if the relevant time stamp is valid, on a subsequent reboot shortly after they won't run (because they already have been run).

Agreed.

However, in my case and possibly the o/p's, these symptoms **only** happen after a session where updates or app installs are done.

You can run for a week, a month, with no symptoms then update or install an app and bang, next boot shows high ram use which doesn't get released.

The behaviour is consistently reproducible. 

If you then reboot all is fine again and dandy and stays that way until you next update or install an app.

---

### Post by caribo on 2010-07-15
+1 
 
I experience the exact same problems and have done with lucid 10.04 release and lately Maverick. There is no way to establish what processes is using memory as it is not accounted for in system monitor. The follwoing commands look like they may be useful, but to be honest I don't understand all of the details..
 
cat /proc/meminfo
cat /proc/slabinfo
vmstat -m (assuming you have vmstat installed)
 
I suspect that it is something to do with ureadahead, but the memory remains allocated after ureadahead has finished... maybe something to do with the kernel?
 
For me, I can recreate the problem by rebooting the system repeatedly without applying any updates. I guess that around 70% of the time it is ok with memory usage (used by programs) as low as 170MB, the other 30% memory usage (used by programs) is around 400MB. Buffer and cache memory stats remain pretty consistent regardless.
 
:-(
 
This bug may be related..
 
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)
 
It suggests that ureadahead is not freeing kernel tracing memory. Tracing memory is a new feature and does not get accounted for in ps / htop / system monitor etc.
 
The following command is claimed to return the allocated tracing memory to the system.
 
echo 1|sudo tee /sys/kernel/debug/tracing/buffer_size_kb

I have tested this and can confirm that it works.

*NB This appears to have been fixed in lucid-proposed repo. (ureadahead_0.100.0-4.1.2)

---

