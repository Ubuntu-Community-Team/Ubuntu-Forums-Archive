---
title: "Ubuntu 11.10 Conky CPU Temperature"
date: 2011-11-20
forum: General Help
---

### Post by ShodanjoDM on 2011-11-20
I've noticed for some time that the CPU temperature reading in 11.10 as shown in Conky is higher than 11.04 and also other distros in my PC (Arch & OpenSUSE 12.1). In 11.10, the temperature is around 48-50C during idle where in 11.04 and other distros it hovers around 37-39C.

But although the reading is higher, the fan is still running at the same speed. So it might be just a bug in Conky although I'm not really sure about it.

Have anyone experience the same?

My CPU is AMD Phenom II X4 945 - 3.0Ghz.

---

### Post by ds5v50 on 2011-11-20
Have you tried rebooting the pc and looking in the bios to confirm the temp matches conky or not? the temp is likely not to change much on a reboot that you will not be able to get and accurate comparison.

---

### Post by Bobhuber on 2011-11-20
> **ShodanjoDM said:**
> I've noticed for some time that the CPU temperature reading in 11.10 as shown in Conky is higher than 11.04 and also other distros in my PC (Arch & OpenSUSE 12.1). In 11.10, the temperature is around 48-50C during idle where in 11.04 and other distros it hovers around 37-39C.

But although the reading is higher, the fan is still running at the same speed. So it might be just a bug in Conky although I'm not really sure about it.

Have anyone experience the same?

My CPU is AMD Phenom II X4 945 - 3.0Ghz.
I'm not sure where Conky gets its readings from but most likely lm-sensors.
The lm-sensors readings vary quite a bit depending on which Distro and even differ in Ubuntu releases. The 37-39C is about right for your CPU. You can adjust the readout by making entries in /etc/sensors3.conf.
From a terminal run > sensors .  This will give you the cpu chipset and temps.
Then you can add the adjustments by modifying the /etc/sensors3.conf file.
Heres mine but please note I am ADDING 10C to my readings where you may need to subtract .
```
chip "k10temp-*"

    compute temp1 @+10,@-10
    compute temp2 @+10,@-10
    compute temp3 @+10,@-10
    compute temp4 @+10,@-10
```Google lmsensors for a complete explanation of whats going on - rather lengthy.

---

### Post by ShodanjoDM on 2011-11-20
> **ds5v50 said:**
> Have you tried rebooting the pc and looking in the bios to confirm the temp matches conky or not? the temp is likely not to change much on a reboot that you will not be able to get and accurate comparison.

It's around 35-37 in bios, so conky reading in 11.10 is way off. Oh, and as precaution, I have cleaned the cpu fan and heatsink a couple of days ago but the reading still stays the same.

> **Bobhuber said:**
> I'm not sure where Conky gets its readings from but most likely lm-sensors.
The lm-sensors readings vary quite a bit depending on which Distro and even differ in Ubuntu releases. The 37-39C is about right for your CPU. You can adjust the readout by making entries in /etc/sensors3.conf.
From a terminal run > sensors .  This will give you the cpu chipset and temps.
Then you can add the adjustments by modifying the /etc/sensors3.conf file.
Heres mine but please note I am ADDING 10C to my readings where you may need to subtract .
```
chip "k10temp-*"

    compute temp1 @+10,@-10
    compute temp2 @+10,@-10
    compute temp3 @+10,@-10
    compute temp4 @+10,@-10
```Google lmsensors for a complete explanation of whats going on - rather lengthy.

sensors reading in terminal (default):

```
f71889ed-isa-0500
Adapter: ISA adapter
+3.3V:        +3.33 V  
in1:          +0.99 V  (max =  +2.04 V)
in2:          +1.61 V  
in3:          +0.96 V  
in4:          +1.09 V  
in5:          +1.29 V  
in6:          +1.28 V  
3VSB:         +3.23 V  
Vbat:         +3.18 V  
fan1:        3546 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
temp1:        +46.0°C  (high = +255.0°C, hyst = +251.0°C)  ALARM (CRIT)
                       (crit = +255.0°C, hyst = +251.0°C)  sensor = transistor
temp2:          FAULT  (high = +255.0°C, hyst = +251.0°C)
                       (crit = +255.0°C, hyst = +251.0°C)  sensor = transistor
temp3:        +39.0°C  (high = +255.0°C, hyst = +253.0°C)  ALARM (CRIT)
                       (crit = +255.0°C, hyst = +253.0°C)  sensor = transistor

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +35.0°C  (high = +70.0°C)
```

Then I added k10temp and the values in /etc/sensors3.conf with:

```

chip "k10temp-*"
compute temp1 (@ + 10), (@ - 10)
compute temp2 (@ + 10), (@ - 10)
compute temp3 (@ + 10), (@ - 10)
compute temp4 (@ + 10), (@ - 10)
```

The value that you gave: compute temp1 @+10,@-10 didn't work, it gave reading error. So I googled a bit and found the lines [here]("http://www.lm-sensors.org/wiki/Configurations/MSI/GF615M-P33").

However after saving the changes, the sensors reading becomes like this:

```
f71889ed-isa-0500
Adapter: ISA adapter
+3.3V:        +3.33 V  
in1:          +0.99 V  (max =  +2.04 V)
in2:          +1.61 V  
in3:          +0.96 V  
in4:          +1.09 V  
in5:          +1.29 V  
in6:          +1.28 V  
3VSB:         +3.23 V  
Vbat:         +3.18 V  
fan1:        3562 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
temp1:        +46.0°C  (high = +255.0°C, hyst = +251.0°C)  ALARM (CRIT)
                       (crit = +255.0°C, hyst = +251.0°C)  sensor = transistor
temp2:          FAULT  (high = +255.0°C, hyst = +251.0°C)
                       (crit = +255.0°C, hyst = +251.0°C)  sensor = transistor
temp3:        +39.0°C  (high = +255.0°C, hyst = +253.0°C)  ALARM (CRIT)
                       (crit = +255.0°C, hyst = +253.0°C)  sensor = transistor

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +44.5°C  (high = +80.0°C)
```

While conky reading still stays the same. Now its showing 47C...

---

### Post by stinkeye on 2011-11-20
What's your line in conky to show cpu temp?
Try a few of the different readings and test to see which is the right one.
eg when I open up a few programs at
the same time the temp goes up 5-6 degrees.

---

### Post by ShodanjoDM on 2011-11-20
Conky entry for cpu temp:

```
		CPU Freq: ${freq_g} Ghz
		CPU Temp: ${hwmon temp 1} C${alignr} 

```

---

### Post by stinkeye on 2011-11-20
The last temp1 reading looks closest to your bios.

Try using for cpu...
Test in terminal...
```
sensors | tail -1 | awk '{print $2}' | cut -c2-3
```

If it works... line for conky (replace **${hwmon temp 1}**)
```
${execpi [COLOR="Red"]5[/COLOR] sensors | tail -1 | awk '{print $2}' | cut -c2-3}
```
[COLOR="red"]Update interval in secs[/COLOR]

May want to remove the temp values you added to  /etc/sensors3.conf

---

### Post by ShodanjoDM on 2011-11-20
Thanks, it appears that instead of taking reading from k10temp, the conky config that I have is taking its reading from f71889ed-isa-0500. Don't know why it's so different compared to other distros and Ubuntu 11.04 though.

However, I've found the fix in here:

[http://ubuntuforums.org/showpost.php?p=11013044&postcount=18302](http://ubuntuforums.org/showpost.php?p=11013044&postcount=18302)

Now I've changed the hwmon line slightly and conky reading match the output of sensors command in the terminal.

Thank you everyone. I'm marking this thread as solved.

---

