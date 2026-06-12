---
title: "system temperature"
date: 2009-07-01
forum: General Help
---

### Post by mkrahmeh on 2009-07-01
am running an application that takes some time to execute, which causes the laptop's fan to start spinning. by that time, when i check the temperature figures for the cpu and HDD using
```
cat /proc/acpi/thermal_zone/TZS0/temperature

cat /proc/acpi/thermal_zone/TZS1/temperature

sudo hddtemp /dev/sda
```

i find high temperatures like 70 - 75
but once the program finishes execution, i check the temperature immediately, and i find that the figures fall to 50 - 55..
so i guess these figures are not precise..right ?

if not, is there a way to monitor the laptop's temp reliably ? 
thx

---

### Post by colau on 2009-07-01
> **mkrahmeh said:**
> am running an application that takes some time to execute, which causes the laptop's fan to start spinning. by that time, when i check the temperature figures for the cpu and HDD using
```
cat /proc/acpi/thermal_zone/TZS0/temperature

cat /proc/acpi/thermal_zone/TZS1/temperature

sudo hddtemp /dev/sda
```

i find high temperatures like 70 - 75
but once the program finishes execution, i check the temperature immediately, and i find that the figures fall to 50 - 55..
so i guess these figures are not precise..right ?

if not, is there a way to monitor the laptop's temp reliably ? 
thx

[http://linuxpoison.blogspot.com/2008/06/monitor-your-hardware-temperature.html](http://linuxpoison.blogspot.com/2008/06/monitor-your-hardware-temperature.html)

[http://blog.mypapit.net/2008/06/monitor-temperature-from-ubuntu-linux-gnome-applet.html](http://blog.mypapit.net/2008/06/monitor-temperature-from-ubuntu-linux-gnome-applet.html)

---

### Post by mkrahmeh on 2009-07-01
thx colau
but i forgot to mention that i use KDE not gnome, however i tried to work the computertemp applet but it ddnt work

note: i tried the ktemperature, which is a KDE applet, but it uses the info in /proc/acpi/thermal_zone/TZS*/temperature, and so does the gnome-applets i guess..
if all applets/programs use the same approach, i dont think this will solve the problem..unless the CPU's temp can really drop 20 degrees in less than a second !

---

### Post by niteshifter on 2009-07-01
> **mkrahmeh said:**
> 
if all applets/programs use the same approach, i dont think this will solve the problem..unless the CPU's temp can really drop 20 degrees in less than a second !

Ever see an incandescent light bulb? When on that filament is white hot (~3000C), but when switched off it drops in 100's of milliseconds to envelope temperatures (<100C).

Much the same for CPUs: what is being reported is the temperature of the "die" aka the silicon structure via embedded diode, not the case. Yes it can drop that fast, especially on variable frequency CPUs with on demand speed shifting (default behavior in the generic kernel). App pushes CPU to higher speed, die heats up. When demand drops the die rapidly drops to case temperature. Just like the light bulb.

---

