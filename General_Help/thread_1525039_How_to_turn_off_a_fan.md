---
title: "How to turn off a fan"
date: 2010-07-06
forum: General Help
---

### Post by asd123asd on 2010-07-06
On Windows I use software called SpeedFan to turn off a fan that does a whole lot of noise but has no effect on system temperature.
[IMG]http://img191.imageshack.us/img191/6804/speedfan.png[/IMG]

How do I go about turning it off on Ubuntu (Lucid Lynx)? Wine does not support this program.

---

### Post by amauk on 2010-07-06
silly question,
but why not just remove / unplug the fan?

*edit*
or maybe move it so it's in a better position

---

### Post by okplayer02 on 2010-07-06
you could also install the applet to control your processor which can clock down your processor speed so it doesnt run hot. so no need for the fan to kick in. 

Its called the CPU frequency scaling monitor.

---

### Post by 3rdalbum on 2010-07-06
I think the best idea is to unplug the fan. There are one or two command-line utilities for controlling fan speeds in Linux, but they are little-known because most people just tell their BIOS to control the fan speed... it's safer and more efficient.

---

### Post by asd123asd on 2010-07-06
It's actually CPU's vent. When I turn it to 0 in SpeedFan it actually doesn't stop and I think thats what keeps the temp stable. 

Yes, you can suggest that I replace it, but I'm still looking for a temporary solution.

---

### Post by asd123asd on 2010-07-06
> **3rdalbum said:**
> I think the best idea is to unplug the fan. There are one or two command-line utilities for controlling fan speeds in Linux, but they are little-known because most people just tell their BIOS to control the fan speed... it's safer and more efficient.

What might those utilities be? My BIOS is very limited and I really don't feel like flashing for this small problem.

---

### Post by asd123asd on 2010-07-13
Is bumping allowed? It's been like a week and no answers. :(

---

### Post by mkvnmtr on 2010-07-13
Good luck. I have been on this forum quite some time and have never seen a good answer to your question.

---

### Post by cascade9 on 2010-07-13
[http://wiki.archlinux.org/index.php/Fan_Speed_Control](http://wiki.archlinux.org/index.php/Fan_Speed_Control)

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29)

Yes, I know, arch and an obsolete version of ubuntu, but it should at least get you started. 

BTW, you could always just see if the fan will spin at 5v or 7v. If it does, remove it from the motherboard headers, and connect it to a molex at 5v or 7v. Heres how you can do that (and you dont need half the equipment they used on this page, but its not a bad guide at all)- 

[http://www.techpowerup.com/articles/other/137](http://www.techpowerup.com/articles/other/137)

---

