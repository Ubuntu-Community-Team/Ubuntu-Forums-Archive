---
title: "lm-sensors threshold"
date: 2011-04-13
forum: General Help
---

### Post by lijcam on 2011-04-13
Hi All, 

I'm having a problem with lm-sensors where it will drop what the max threshold values for some sensors which causes the daemon the spam the syslog. The only way I can seem to find to restore them is to restart the whole machine however being a NAS its not really a good solution.

It only seems to occur on this chip the other two are fine.

For example;
After a reboot the output from sensors is
```
w83627dhg-isa-0ca0
Adapter: ISA adapter
Vcore:       +1.16 V  (min =  +0.72 V, max =  +1.39 V)
+1.05V:      +1.05 V  (min =  +0.94 V, max =  +1.16 V)
AVCC:        +3.36 V  (min =  +2.96 V, max =  +3.63 V)
3VCC:        +3.36 V  (min =  +2.98 V, max =  +3.63 V)
Vdimm:       +1.84 V  (min =  +1.62 V, max =  +1.98 V)
+5V:         +5.15 V  (min =  +4.51 V, max =  +5.50 V)
+12V:       +11.78 V  (min = +10.75 V, max = +13.18 V)
3VSB:        +3.30 V  (min =  +2.96 V, max =  +3.63 V)
Vbat:        +3.14 V  (min =  +2.96 V, max =  +3.63 V)
Case Fan:    827 RPM  (min =  712 RPM, div = 8)
MB Temp:     +41.0Â°C  (high = +75.0Â°C, hyst = +70.0Â°C)  sensor = thermistor
CPU Temp:    +46.0Â°C  (high = +90.0Â°C, hyst = +87.0Â°C)  sensor = diode
Case Temp:   +30.5Â°C  (high = +80.0Â°C, hyst = +75.0Â°C)  sensor = diode
```

However after a while it will start to look like this.

```
w83627dhg-isa-0ca0
Adapter: ISA adapter
Vcore:       +1.16 V  (min =  +0.72 V, max =  +1.39 V)
+1.05V:      +1.05 V  (min =  +0.94 V, max =  +0.00 V)   ALARM
AVCC:        +3.36 V  (min =  +0.00 V, max =  +3.63 V)
3VCC:        +3.36 V  (min =  +0.00 V, max =  +0.08 V)   ALARM
Vdimm:       +1.84 V  (min =  +1.62 V, max =  +1.98 V)
+5V:         +5.15 V  (min =  +4.51 V, max =  +5.50 V)
+12V:       +11.78 V  (min = +10.75 V, max =  +0.00 V)   ALARM
3VSB:        +3.30 V  (min =  +2.96 V, max =  +3.63 V)
Vbat:        +3.14 V  (min =  +2.96 V, max =  +3.63 V)
Case Fan:      831 RPM  (min =    0 RPM, div = 128)
MB Temp:     +41.0Â°C  (high = +78.0Â°C, hyst = +70.0Â°C)  sensor = thermistor
CPU Temp:    +46.0Â°C  (high = +90.0Â°C, hyst =  +0.0Â°C)  sensor = diode
Case Temp:   +30.0Â°C  (high =  +0.0Â°C, hyst =  +0.0Â°C)  ALARM  sensor = diode
```

Here is what is in the config
```
cat /etc/sensors.d/x7spa-hf
chip "w83627dhg-*"

        label in0 "Vcore"
        label in1 "+1.05V"
        label in2 "AVCC"
        label in3 "3VCC"
                set in3_min 3.3 * 0.90
                set in3_max 3.3 * 1.10
        label in4 "Vdimm"
        label in5 "+5V"
                compute in5 @*4, @/4
        label in6 "+12V"
                compute in6 @*16, @/16
                set in6_min 12 * 0.90
                set in6_max 12 * 1.10
        label in7 "3VSB"
        label in8 "Vbat"

        ignore fan1
        ignore fan2
        ignore fan3
        label fan4 "Case Fan"
        ignore fan5

        label temp1 "MB Temp"
        label temp2 "CPU Temp"
        label temp3 "Case Temp"

        ignore cpu0_vid

```

---

