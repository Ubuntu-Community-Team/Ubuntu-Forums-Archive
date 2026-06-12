---
title: "Voltage ALARMS using lm-sensors"
date: 2011-07-14
forum: General Help
---

### Post by junglist313 on 2011-07-14
So I installed lm-sensors, probed, run sensors get this:

```
$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +24.8°C  (high = +70.0°C, crit = +67.0°C)  

it8720-isa-0228
Adapter: ISA adapter
in0:         +1.22 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.66 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.38 V  (min =  +0.00 V, max =  +4.08 V)   
+5V:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +3.07 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +2.22 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +4.08 V  (min =  +0.00 V, max =  +4.08 V)   ALARM
5VSB:        +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.26 V
fan1:       3358 RPM  (min =    0 RPM)
fan2:       1374 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +34.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +36.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:       +36.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +0.513 V


```

Should I be worried about that ALARM? I put this box together, is this something I can open up and fix, or will I have to replace parts? I know that there is a short somewhere in the front panel usb port on my case, could that be the problem?

---

