---
title: "Confused by temperature sensors."
date: 2010-08-12
forum: General Help
---

### Post by bobtfish on 2010-08-12
On my laptop hardinfo works fine, showing two temperatures (dual core) by default, without me having to do anything. I just set up a new tower, and hardinfo didn't show anything in the sensors at all, so I did some searching and installed a package to get access to hardware sensors, but now I'm quite confused by the results.
See the attached picture: Hardinfo pretty much gives me gibberish. The AWN hardware sensors applet is better, but still shows some stuff that confuses me.
So, any advice on how to find out what the non-obvious temperatures are? And how to get the useful ones (core temperatures and GPU temperature) to appear in hardinfo? I don't particularly want to use the AWN applet, so being able to access this information elsewhere would be a big plus.
Also, I've never used it before so I don't really know how it works, but "acpi -t" doesn't return anything at all.
Thanks.
Chris

---

### Post by acidx on 2010-08-14
I've tried to understand why HardInfo repeats some sensors, but failed to do so, as I was unable to reproduce this on any machines I have access to debug. :(

Anyway, I'll check out how AWN does its stuff and perhaps add another method of gathering CPU/GPU temperatures, as I haven't touched that part of the code for a while and there might be new methods of obtaining the temperatures/FAN speeds.

BTW, there is a "Report bug" option in the Help menu. Please use it whenever you find a bug in HardInfo: I'm not a forum reader and only caught your post by chance.

---

### Post by bobtfish on 2010-08-15
Thanks for replying. I might not be using the most recent version of hardinfo anyway, it's from the main repository. I'm normally not much for bug reports, I usually assume it's me doing something wrong and try to solve that first, but I'll make sure to report stuff in future.
Is there any way to find out what hardware the temperatures are supposed to be for? Temp's 1 and 2 and continuously stuck at -55 and -2 degrees, which are clearly rubbish.

---

### Post by Vaphell on 2010-08-15
sensors report bunch of numbers that have to be translated into a human readable form. Apparently formula in your case is incorrect. Sensors may even be unsupported entirely (not detected).
For example, my box tells me next to nothing, because sensors in phenomII cpus/am3 mobos are not supported yet in the standard sensor package.

---

### Post by acidx on 2010-08-15
> **bobtfish said:**
> Is there any way to find out what hardware the temperatures are supposed to be for? Temp's 1 and 2 and continuously stuck at -55 and -2 degrees, which are clearly rubbish.

The name for the tempeatures comes from the lm-sensors configuration file in your case. I have no way to know which sensor corresponds to which device on your computer, except by maintaining enormous tables by myself, which is complicated as there are so many mother boards out there :)

Try running "sensors" on your terminal and pasting the output here (or better, in the bug report you filed, it'll be easier to find it later). If the output is different from HardInfo, it might be another bug, as I might not be applying the correct formula.

---

### Post by bobtfish on 2010-08-16
Thanks for the input. Running sensors gives:
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +37.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +32.0°C  (high = +76.0°C, crit = +100.0°C)  

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.07 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.79 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.39 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +2.96 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.43 V  (min =  +0.00 V, max =  +2.10 V)   
in5:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
in7:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.07 V
fan1:        918 RPM  (min =    0 RPM)
fan2:       2721 RPM  (min =    0 RPM)
temp1:       -55.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:       +20.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
cpu0_vid:   +3.300 V

```

Now the 3 temperatures at the bottom do match those given in HardInfo, so it seems the sensors themselves are reporting weird things. I guess I'll just ignore those then. Although I notice that the first 2 are apparently thermistors, giving weird results, whereas the 3rd is a thermal diode, giving a reasonably sensible output, whatever it may be for. Maybe the thermistors aren't supported or configured correctly?? I'll do some digging on this.

However, there are 2 temperatures at the top of this output for cores that do not appear in HardInfo (but do in AWN). Is there any way I can get them to appear via configuration files or something? Or is this hard coded? Which unfortunately would be way out of my abilities.

---

