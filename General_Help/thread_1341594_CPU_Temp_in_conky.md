---
title: "CPU Temp in conky"
date: 2009-11-29
forum: General Help
---

### Post by Meskarune on 2009-11-29
how do I add cpu tempurature to conky?

I have an intel dual core cpu and installed lm_sensors.

Here is the output of sensors:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +40.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +41.0°C  (high = +78.0°C, crit = +100.0°C)  

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:       +3.34 V
in1:         +1.13 V  (max =  +2.04 V)   
in2:         +0.92 V
in3:         +0.77 V
in4:         +0.98 V
in5:         +1.13 V
in6:         +0.93 V
3VSB:        +3.34 V
Vbat:        +3.30 V
fan1:        887 RPM
fan2:          0 RPM  ALARM
fan3:          0 RPM  ALARM
fan4:          0 RPM  ALARM
temp1:       +27.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:       +35.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +95.0°C, hyst = +91.0°C)  sensor = thermistor
temp3:       +33.0°C  (high = +70.0°C, hyst = +68.0°C)  
                      (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor
```

Here's my conky:

[http://lh3.ggpht.com/_o7Z-H36cyiE/SxM6WWNOiWI/AAAAAAAADgM/B-rNjUIDKao/s576/conky.jpg]("http://lh3.ggpht.com/_o7Z-H36cyiE/SxM6WWNOiWI/AAAAAAAADgM/B-rNjUIDKao/s576/conky.jpg")

---

### Post by Meskarune on 2009-11-29
I probably should have fuzzed out my ip address. opps.

---

### Post by Meskarune on 2009-12-05
no one can help me out?

---

### Post by wojox on 2009-12-05
Add this above the TEXT:

```

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

```

And below

```

CPU1: ${cpu cpu1}%${alignr}${cpubar cpu1 8,70}
CPU2: ${cpu cpu2}%${alignr}${cpubar cpu2 8,70}

```

---

