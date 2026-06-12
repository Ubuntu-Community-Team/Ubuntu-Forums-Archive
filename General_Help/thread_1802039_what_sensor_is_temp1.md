---
title: "what sensor is temp1?"
date: 2011-07-11
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-07-11
this sensor appeared after i updated my kernel so my guess was i was unable to see it before but i don't know what the sensor goes to
is there anyway i can figure out what the sensor goes to?

---

### Post by Mark Phelps on 2011-07-11
It's most probably a consolidation of the temps of ALL the cores in your CPU. I have a multi-core AMD and lm-sensors only reports one core temp -- which seems to be the average of all the cores.

---

### Post by pqwoerituytrueiwoq on 2011-07-11
i am running a quad core and temp one is not the processor since i already have a processor temperature
if each my cores had its own temp (like my laptop) i would have 4 temps not 2
my hardware info is in my signature
this sensor's readout changes more than any other one in the system
edit:
```
chad@lucid-desktop:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +30.0°C  (high = +70.0°C, crit = +90.0°C)  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +0.92 V  (min =  +0.85 V, max =  +1.70 V)
 +3.3 Voltage:       +3.46 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.11 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.54 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      2213 RPM  (min =  600 RPM)
CHASSIS FAN Speed:   891 RPM  (min =  600 RPM)
CHASSIS FAN 2 Speed:2184 RPM  (min =  600 RPM)
CPU Temperature:     +32.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:      +29.0°C  (high = +45.0°C, crit = +75.0°C)
```
does that mean it is the pci slot my gpu is in?
it is the only card i am using

---

