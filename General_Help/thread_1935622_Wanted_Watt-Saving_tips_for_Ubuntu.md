---
title: "Wanted: Watt-Saving tips for Ubuntu"
date: 2012-03-04
forum: General Help
---

### Post by misterbk on 2012-03-04
Anyone have suggestions how I can get better power-saving options in Ubuntu / Kubuntu?


For example, in Windows I can tell the system to downclock the CPU when it's idle, power down unused cores, manage when disks spin down, and a LOT of other things.

In Linux, I have options to:

* "sleep after x minutes" (can't do this, the box needs to run cron jobs at certain times of day)

* "Turn off screen after X minutes"  (currently enabled.)

* "Disable desktop effects after X minutes"  (nice, but introduces a delay on the next mouse movement, and doesn't decrease power consumption.)


Is that really all I can do?  System is currently drawing 70 watts when sitting idle, not including the screen.

---

### Post by MG&amp;TL on 2012-03-04
You might want to have a look at the Jupiter applet. Designed to reduce the CPU when you don't need it.

[http://www.jupiterapplet.org/](http://www.jupiterapplet.org/)

---

### Post by misterbk on 2012-03-06
Still trying to figure out what exactly Jupiter can do for me...

This is a 'kiosk' type device. Always on, hosts a few Samba volumes, 90% of its duties are to start playing music at certain times of day and be an entertainment / music center (i.e. Pandora, Hulu / YouTube / whatever on the TV.)

So, not a laptop, and thus no Bluetooth / WiFi / screen dimming etc.

I guess it puts a 'hook' somewhere, but no indication what that is or what it does?


The link was very helpful however, led me here:
[http://lesswatts.org/](http://lesswatts.org/)

Lots of interesting power saving tips on that site.  

Some of the most interesting things were the discussions of P-States and process scheduler modifications.  I want to try and target only one core of the CPU until that core fills up, and only then start using additional cores.  (This ought to let the other cores go to sleep.)

Windows can also downclock the CPU when idle, which may be the P-states thing.  I'll see what I can find.

---

### Post by fuduntu on 2012-03-07
> **misterbk said:**
> Still trying to figure out what exactly Jupiter can do for me...

This is a 'kiosk' type device. Always on, hosts a few Samba volumes, 90% of its duties are to start playing music at certain times of day and be an entertainment / music center (i.e. Pandora, Hulu / YouTube / whatever on the TV.)

So, not a laptop, and thus no Bluetooth / WiFi / screen dimming etc.

I guess it puts a 'hook' somewhere, but no indication what that is or what it does?


The link was very helpful however, led me here:
[http://lesswatts.org/](http://lesswatts.org/)

Lots of interesting power saving tips on that site.  

Some of the most interesting things were the discussions of P-States and process scheduler modifications.  I want to try and target only one core of the CPU until that core fills up, and only then start using additional cores.  (This ought to let the other cores go to sleep.)

Windows can also downclock the CPU when idle, which may be the P-states thing.  I'll see what I can find.

Jupiter won't really do anything for you unless you are running on battery.  You can tune Jupiter to apply the same tweaks while you are plugged in, but at that point you may as well just put them in rc.local.

---

### Post by misterbk on 2012-03-08
> **fuduntu said:**
> Jupiter won't really do anything for you unless you are running on battery.  You can tune Jupiter to apply the same tweaks while you are plugged in, but at that point you may as well just put them in rc.local.

That would be the way to go then.

I followed almost all of the tips on lesswatts.org that sounded like they might save power, and gained 7 watts from spinning down a hard drive but nothing else.  Does Jupiter App do anything other than these that might save power?

(7 watts saved!)  - Told secondary hard drive (archive volume hosted via Samba) to spin down after inactivity.
(no savings) - Tried activating power save on sound card.
(no savings) - Tried turning gigabit down to 100 megabit.
(no savings) - Kernel is already on the cpufreq ondemand governor.
(no savings) - Desktop effects
(Tiny savings) - Modified scheduler preferences to have a higher threshold for choosing to boost CPU clock under load, so CPU stays at low clock for most things.


I wanted to modify the scheduler to target cores one at a time, allowing the remaining three to sleep... but the configurable wasn't present in /sys/devices/system/cpu/.

I had this configurable, which lesswatts says is for multi-socket (this is a single-cpu system and not Xeon):
_*/sys/devices/system/cpu/sched_smt_power_savings*_

but not this one, which it said was for multi-core:
_*/sys/devices/system/cpu/sched_mc_power_savings*_

(ref _**[this page]("http://lesswatts.org/tips/cpu.php")**_, at the top)

I set sched_smt_power_savings to 1, but it did not seem to make a difference.  In top I see cores 2,3,4 all getting small percentages of activity.


Currently the system is down to 63 watts when navigating KDE with desktop effects, browsing lightweight web pages in firefox and playing Pandora.
[EDIT: 63 watts is also the minimum power usage when fully idle.]

Specs:
MB  ASROCK Z68 PRO3-M Z68 LGA1155
MEM 4G CORSAIR DDR3 (one slot only)
CPU INTEL CORE I3 2125 3.3Ghz
HD  WD BLACK 1TB 7200RPM (primary)  <-- does not support APM, probably adds 10 watts...
HD  HITACHI 2TB 5400RPM (secondary, archive drive)

---

