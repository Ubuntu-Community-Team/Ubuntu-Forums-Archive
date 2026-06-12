---
title: "thermal sensor question"
date: 2012-01-19
forum: General Help
---

### Post by cain071546 on 2012-01-19
[house@archbang ~]$ sensors
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +38.0°C  
Core1 Temp:   +34.0°C  

it8716-isa-0290
Adapter: ISA adapter
in0:          +1.49 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.82 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.25 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.90 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +2.94 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +3.14 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +1.09 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +2.90 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +1.07 V  
fan1:           0 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
temp1:        +32.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +38.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +21.0°C  (low  = +127.0°C, high = +60.0°C)  sensor = thermal diode
cpu0_vid:    +1.475 V
intrusion0:  OK

[house@archbang ~]$ 


which one is my CPU Temp? 1,2,3???
and if the cpu temps are at the top up there^ what are temps 1,2,3 for?

i just wanna make my temps show in a conky but im unsure of which temp to tell conky to display

---

### Post by dcstar on 2012-01-20
> **cain071546 said:**
> 
..........
which one is my CPU Temp? 1,2,3???
and if the cpu temps are at the top up there^ what are temps 1,2,3 for?

i just wanna make my temps show in a conky but im unsure of which temp to tell conky to display

Reboot and look at the BIOS screen that tells you these things.

---

### Post by xyzzyman on 2012-01-20
k8temp-pci-00c3 is your CPU, and core0 & core1 are your two cores as you probably have an Athlon 64 X2. 

When you reboot to bios the temps are likely to change by then, but it may give you a better description of the other temps. I take it this isn't an OEM system, and more of a custom built? The other temps are probably a temp on the mobo itself and possibly a north or south bridge temperature.

---

