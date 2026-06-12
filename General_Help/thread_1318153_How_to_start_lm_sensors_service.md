---
title: "How to start lm_sensors service?"
date: 2009-11-07
forum: General Help
---

### Post by amille41 on 2009-11-07
Yes, I've already searched for solutions on google before coming here but the only solution was to execute:

"lm_sensors start" which returns "lm_sensors: command not found"

Also a whereis lm_sensors didn't find anything. I downloaded and compiled lm_sensors 3.1.1 for Xubuntu 9.10 and ran sensors-detect successfully. Running sensors gives me this output:

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.20 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:      +3.25 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +5.14 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.03 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      958 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:   0 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:   0 RPM  (min =  600 RPM)
CHASSIS3 FAN Speed:   0 RPM  (min =  600 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM)
CPU Temperature:    +41.0°C  (high = +60.0°C, crit = +75.0°C)  
MB Temperature:     +45.0°C  (high = +45.0°C, crit = +75.0°C)

So I think lm_sensors has found my hardware. How do I start the service?

---

### Post by lovinglinux on 2009-11-07
[http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/](http://www.techthrob.com/2009/03/02/enabling-hardware-sensors-in-linux/)

---

### Post by amille41 on 2009-11-07
That worked, much appreciated.

---

