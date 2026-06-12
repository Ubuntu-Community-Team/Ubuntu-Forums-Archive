---
title: "Sensors command output"
date: 2011-03-30
forum: General Help
---

### Post by conradin on 2011-03-30
Hi all,
I'm running an i7 960 with all cores maximised but not over clocked. 
 Im using sensors to map the temprateure but im not sure about what the output means. I have a Corsair H50 liquid cooling unit, and Im not impressed. though according to the data sheet, 67C is the expected operation temp. 

My question is what do the high and crit temps mean? Are those temps the CPU has reached?
Core 0:      +60.0°C  (high = +80.0°C, crit = +100.0°C)  

would I be better off with a stock fan??

```

~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.24 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:      +3.25 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.05 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +11.69 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     1562 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:   0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:1394 RPM  (min =  600 RPM)
CHASSIS3 FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM)
CPU Temperature:    +54.0°C  (high = +60.0°C, crit = +75.0°C)  
MB Temperature:     +43.0°C  (high = +45.0°C, crit = +75.0°C)  
MCH Temperature:     +0.0°C  (high = +60.0°C, crit = +95.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +60.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +57.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +61.0°C  (high = +80.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +59.0°C  (high = +80.0°C, crit = +100.0°C)  


```

---

### Post by blueridgedog on 2011-03-30
They are limits in your lmsensors config file:

[http://www.lm-sensors.org/wiki/FAQ/Chapter3#HowdoIsetnewlimits](http://www.lm-sensors.org/wiki/FAQ/Chapter3#HowdoIsetnewlimits)

---

### Post by conradin on 2011-04-01
Ah, ok.
I disabled multithreading, and I'm seeing only a small amount of throughput loss. additionally, maxed out for hours on end, the temp is stable at 47C much better than 60C before. Normal load, temps stable at 32C.

---

