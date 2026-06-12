---
title: "Measuring CPU temperature"
date: 2011-04-24
forum: General Help
---

### Post by thomas515 on 2011-04-24
I have an HP laptop with Ubuntu 10.10.  Is there a way to view the CPU temperature without needing additional hardware?

---

### Post by flipper T on 2011-04-24
read this

[http://www.ehow.com/how_6651224_monitor-cpu-temperature-ubuntu.html](http://www.ehow.com/how_6651224_monitor-cpu-temperature-ubuntu.html)


google search is wonderful btw

---

### Post by apochry on 2011-04-24
Synaptic --> Search "computertemp" (computer temperature monitor applet for GNOME) --> Install --> Close

Gnome Panel + Right click --> Add to Panel... --> Computer Temperature Monitor --> Add

Keep mouse for 2 secs over the applet icon in the panel --> See the core-temps.
In the Preferences of the Applet you can change the Display Mode (Graphic/Text/Both). There are also an options to log the temps and set an alarm.

Izzo

---

### Post by apochry on 2011-04-26
I guess you have you CPU Temperature already.
**If so, please mark this as [SOLVED].**

Izzo

---

### Post by thomas515 on 2011-04-27
Sorry yeah that worked.

---

### Post by CVGH on 2011-04-27
Nice! Many thanks for this!!!

Brian

---

### Post by PARO on 2011-05-04
yes that's great if you want your temperature updated every 5-15 minutes, and no updates for hours on occasions... anything with live updates out there like CPU Thermometer for Windows?

---

### Post by inameiname on 2011-05-04
watch --interval 1 "cat /proc/acpi/thermal_zone/THRM/*; cat /proc/cpuinfo | grep MHz; cat /proc/acpi/processor/*/throttling"


- it monitors cpu freq and temperature, but does not seem to work with all computers


while sleep 1; do acpi -t | osd_cat -p bottom; done &         

- gets the CPU temperature continuously on the desktop


These are aliases in my bashrc file. May or may not work for you but are worth a shot.

---

### Post by jramshu on 2011-05-04
If you just want to check temps every once in a while you can use this code in terminal.

```
sensors -f
```

You can also open terminal and type this in, it gives a lot of info.

```
byobu
```

To exit byobu just type this

```
exit
```

---

### Post by jramshu on 2011-05-04
Here is a screenshot of byobu.

---

### Post by inameiname on 2011-05-04
```

sensors -f

```

I thank you for this. It is the first that I've found that works for my laptop. Awesome.

---

### Post by PARO on 2011-05-04
Hm.. I re-ran sensors-detect and let it update some file with "core", before i ignored this, but now it seems to be updating every 2 secs as it should, the 2 original bars it has still seem to be updating around 10 minutes or so if at all, and the code "watch --interval 1 "cat /proc/acpi/thermal_zone/THRM/*; cat /proc/cpuinfo | grep MHz; cat /proc/acpi/processor/*/throttling"" gave me that same info, and not updating.  Is the acpi sensor important? or is that the same as the core cpu temp? if its the same i might as well just uncheck it and ignore it i guess. 

byobu shows everything except the temp for me,and shows a red 27! (maybe that is an error code?). the sensors command is giving me one useful temp "core" and one that does not update often if at all called "acpitz-virtual-0
Adapter: Virtual device
temp1"

the coretemp is the only one found though, so i guess as long as that continues working im good. 

Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
Intel Core family thermal sensor...                         No
Intel Atom thermal sensor...                                Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

is it important to have hd temperature monitored, or to have acpi temperature accurately reported? the cooling should work fine without them i imagine? (it seemed to be working fine usually in netbook session, just not in gnome before, but now it seems to be working in gnome too.. time will tell though)

---

### Post by VanR on 2011-05-04
I've been using this.
[http://sensors-applet.sourceforge.net/](http://sensors-applet.sourceforge.net/)

---

