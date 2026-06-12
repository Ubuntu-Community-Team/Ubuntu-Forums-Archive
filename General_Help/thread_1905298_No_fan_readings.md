---
title: "No fan readings"
date: 2012-01-06
forum: General Help
---

### Post by Bobhuber on 2012-01-06
I just replaced my motherboard with an MSI 890GXM to pick up the Sata3 capabilities and a little overclocking .Love it. The only problem I'm having in screenlets or any of the programs that display system readings is the CPU and Chassis fan readout. From a terminal I can see the readouts just fine using the sensors command. The screenlets Meter app shows a fan (fan2  0 RPM that I have removed from the readout) but not the 2 that are actually in use (fan1 & fan3). I've relabeled them in the sensors3 config file along with the temps so I know that the applications are reading the file because they pick up the new names ????  
The chipset > f71889ed-isa-0500 with the drivers (f71882fg) loaded in /etc/modules.
```
 f71889ed-isa-0500
Adapter: ISA adapter
in0:          +1.66 V  
in1:          +1.45 V  (max =  +2.04 V)
in2:          +1.66 V  
in3:          +0.94 V  
in4:          +1.06 V  
in5:          +1.31 V  
in6:          +1.31 V  
in7:          +1.62 V  
in8:          +1.57 V  
Cpu Fan:     1323 RPM
Sys Fan:     1111 RPM
temp1:        +25.0°C  (high = +255.0°C, hyst = +251.0°C)  ALARM (CRIT)
                       (crit = +255.0°C, hyst = +251.0°C)  sensor = transistor
temp2:          FAULT  (high = +255.0°C, hyst = +251.0°C)
                       (crit = +255.0°C, hyst = +251.0°C)  sensor = transistor
Sys Temp:     +38.0°C  (high = +255.0°C, hyst = +253.0°C)  ALARM (CRIT)
                       (crit = +255.0°C, hyst = +253.0°C)  sensor = transistor

k10temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:   +32.0°C  (high = +80.0°C)
                       (crit = +100.0°C, hyst = +98.0°C)


```

I had to manually edit the python file to include the sensor - Have no clue as to why its not being picked up.

---

