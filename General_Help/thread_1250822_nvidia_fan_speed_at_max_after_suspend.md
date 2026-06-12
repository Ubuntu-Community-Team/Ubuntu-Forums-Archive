---
title: "nvidia fan speed at max after suspend"
date: 2009-08-27
forum: General Help
---

### Post by srhlefty on 2009-08-27
If I suspend my computer, and then wake it up, my nvidia graphics card's fan stays at maximum level.  If I log out (or restart X with ctrl-alt-backspace), the fan speed returns to normal.

Is there a way to trigger this without having to restart X every time I wake the computer up?  Like a command to reload the graphics driver or something?

---

### Post by gabak on 2009-08-27
the easy way will be take apart the red wire from the fan 's plug from the video card then plug it in to the power supply conector in the red wire then u will have 5volt and u wont hear the spining from the fan and it will be enough to cool down the heat from the heatshink.

---

### Post by srhlefty on 2009-08-27
> **gabak said:**
> the easy way will be take apart the red wire from the fan 's plug from the video card then plug it in to the power supply conector in the red wire then u will have 5volt and u wont hear the spining from the fan and it will be enough to cool down the heat from the heatshink.

The easy way? And it requires soldering? Surely you are joking sir!

Unless I'm mistaken most of those types of fans operate around 6V at most, which means hooking it directly to the 5V supply would make it sound loud 100% of the time...

---

### Post by gabak on 2009-08-28
u dont have to solder anything just take apart the plug then conect the red wire to the plug of ur PSU in the red color. some of those fans works with 12volt , get a multimeter and take a look.
I have done it many times

> **srhlefty said:**
> The easy way? And it requires soldering? Surely you are joking sir!

Unless I'm mistaken most of those types of fans operate around 6V at most, which means hooking it directly to the 5V supply would make it sound loud 100% of the time...

---

### Post by Nais on 2010-03-16
I've been having the same issue, with the fan running at full speed after waking from suspend. But I've only noticed it since switching to Lucid. My solution was to install nvclock and then readjust the fan speed ```
nvclock -fF 50
``` sets it to 50% which is sufficient for my usage and aural pleasure.

---

### Post by dangmc on 2010-04-22
> **Nais said:**
> I've been having the same issue, with the fan running at full speed after waking from suspend. But I've only noticed it since switching to Lucid. My solution was to install nvclock and then readjust the fan speed ```
nvclock -fF 50
``` sets it to 50% which is sufficient for my usage and aural pleasure.
after installing a geforce 9800 gt I installed nvclock-I keep getting this message when trying to adjust the fan speed. (Your card doesn't support fanspeed adjustments!) Any suggestions? Is there another program? It seems to have a default of 35% which brings idle temps of 55-58c.
Seasonic X-650 psu
Asus P7P55D-E mobo
I5-750 2.66ghz.cpu w/Zalman CNPS 9900 heatsink
4ghz G-Skill F3-12800 ddr3 ram
WD caviar black 1tb.hd
dual boot WinXP and Lucid 10.04 amd64 beta 2
BFG GeForce 9800GT graphics card
 Thank you

---

