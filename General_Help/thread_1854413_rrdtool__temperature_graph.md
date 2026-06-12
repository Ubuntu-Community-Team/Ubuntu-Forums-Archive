---
title: "rrdtool  temperature graph"
date: 2011-10-04
forum: General Help
---

### Post by denis21-ru on 2011-10-04
> $ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +48.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0°C  (high = +78.0°C, crit = +100.0°C)  

it8718-isa-0290
Adapter: ISA adapter
in0:         +1.12 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.81 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.28 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.32 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +0.06 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +2.98 V  (min =  +0.00 V, max =  +4.08 V)   
Vbat:        +3.02 V
fan1:       2616 RPM  (min =    0 RPM)
fan2:          0 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:          0 RPM  (min =    0 RPM)
temp1:       +40.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +27.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +1.219 V


how to derive the temperature of the graphics with rrdtool?

---

