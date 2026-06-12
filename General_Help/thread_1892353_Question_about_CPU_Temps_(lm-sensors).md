---
title: "Question about CPU Temps (lm-sensors)"
date: 2011-12-07
forum: General Help
---

### Post by Lemons on 2011-12-07
Right now I am running ubuntu server 11.10 with a FX-8120 overclocked to 4.0Ghz. When I do a call to sensors, I get:

```
fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       14.23 W  (crit = 124.95 W)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +53.0Â°C  (high = +70.0Â°C)
                       (crit = +90.0Â°C, hyst = +87.0Â°C)

it8721-isa-0290
Adapter: ISA adapter
in0:          +2.76 V  (min =  +2.84 V, max =  +1.24 V)
in1:          +2.86 V  (min =  +0.67 V, max =  +1.33 V)
in2:          +1.27 V  (min =  +0.16 V, max =  +1.45 V)
+3.3V:        +3.24 V  (min =  +0.14 V, max =  +5.06 V)
in4:          +2.11 V  (min =  +1.28 V, max =  +0.89 V)
in5:          +2.48 V  (min =  +2.34 V, max =  +2.83 V)
in6:          +0.53 V  (min =  +2.26 V, max =  +0.55 V)
3VSB:         +4.80 V  (min =  +2.74 V, max =  +1.34 V)
Vbat:         +3.38 V
fan1:        1939 RPM  (min =   33 RPM)
fan2:           0 RPM  (min =   14 RPM)  ALARM
fan3:           0 RPM  (min =   30 RPM)  ALARM
fan5:           0 RPM  (min =   -1 RPM)  ALARM
temp1:        +70.0Â°C  (low  = +36.0Â°C, high = -84.0Â°C)  sensor = thermistor
temp2:        +29.0Â°C  (low  = -32.0Â°C, high = -37.0Â°C)  sensor = thermistor
temp3:       -128.0Â°C  (low  =  -4.0Â°C, high = +73.0Â°C)  sensor = disabled
```

Now, the CPU temp according to the mobo is 70C, quite high. But the processor itself looks to be at 53C according to its sensor. I am trying to get under 62C, and these 2 readings are throwing me off. I have read that the mobo sensors cannot really be trusted as its not on the chip itself, and they use some offsets to get the correct temperature that lm-sensors doesn't know.

My questions are should I be worried the mobo is reporting a high CPU temp and should I use the CPU temp, mobo CPU temp, or a mixture of the two?

Any help is much appreciated, thanks!

---

