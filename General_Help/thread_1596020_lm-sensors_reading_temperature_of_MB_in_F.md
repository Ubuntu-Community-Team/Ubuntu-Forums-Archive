---
title: "lm-sensors reading temperature of MB in F"
date: 2010-10-13
forum: General Help
---

### Post by reffu on 2010-10-13
I know many will say set it to Celsius, but it already is. I believe it is receiving the temperature as Fahrenheit and interpreting it as Celsius. 

This is the output of running sensors:
/```


nick@nick-desktop ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.22 V  (min =  +0.85 V, max =  +1.60 V)
+12V Voltage:      +12.03 V  (min = +10.20 V, max = +13.80 V)
+5V Voltage:        +4.97 V  (min =  +4.50 V, max =  +5.50 V)
+3.3V Voltage:      +3.23 V  (min =  +2.97 V, max =  +3.63 V)
CPU_FAN FAN Speed: 2170 RPM  (min =  800 RPM)
CHA_FAN1 FAN Speed:4017 RPM  (min =  800 RPM)
CHA_FAN2 FAN Speed:   0 RPM  (min =  800 RPM)
PWR FAN FAN Speed:    0 RPM  (min =  800 RPM)
CPU Temperature:    +37.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +106.0°C  (high = +45.0°C, crit = +95.0°C)  

```

As you can see, my MB temperature seems to be over 100 degrees Celsius, which is highly doubtful.
In windows, using speed fan the temperature is usually in the high 30s or low 40s. Any way that anyone knows of fixing this?

Thanks,

Reffu

---

