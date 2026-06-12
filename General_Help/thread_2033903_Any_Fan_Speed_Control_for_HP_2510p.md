---
title: "Any Fan Speed Control for HP 2510p?"
date: 2012-07-27
forum: General Help
---

### Post by vickoxy on 2012-07-27
Hi,
i just bought one HP 2510p and it is really very nice computer with xubuntu 12.04 64bit running very well on it. Still, i wonder, is there some FAn Control app (as thinkfan or fancontrol) with gui (not nevessary) for HP laptops?
I installed lm-sensors and run sensors-detect, but my fan wasn`t recognized.
> linux@linux:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +25.0°C  (crit = +70.0°C)
temp2:        +61.0°C  (crit = +256.0°C)
temp3:        +53.0°C  (crit = +110.0°C)
temp4:        +45.0°C  (crit = +105.0°C)
temp5:        +32.4°C  (crit = +110.0°C)
temp6:        +30.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +53.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:       +53.0°C  (high = +100.0°C, crit = +100.0°C)


So, any idea, how to get fancontrol or some other fan speed control app running on this little machine?

Thanks!

---

### Post by Toz on 2012-07-27
I've owned an HP 8510p and currently use a 6730b. In both cases, the fans didn't show up when running sensors, however, when I did some research a while back, I found out that one of the Virtual Device temperatures is actually the fan speed. Can't remember which one it was though. If your fan changes speeds, keep checking those values and you'll be able to identify it easily enough.

I haven't had any problems (other than dust build-up) with the fan on either of these systems. Is your fan running all of the time or not at all (or are you just looking for fan control)?

Suggestions for fan problems include:
1. using compressed air on the fan itself (one time I had to remove the keyboard to get at a pretty nice-sized dust bunny that made itself a home in there).
2. bios update
3. kernel parameters (e.g. acpi_osi=Linux)

---

### Post by vickoxy on 2012-07-27
Hi, thanks for answers. Well the fan is very quiet, i am just used (had lot of Thinkpads) to have some fan control to keep laptops always quiet. HP2510p is very quiet, but usually i set up the fan to be activated at 70 degrees and above - so normally, i hear no fan.

---

