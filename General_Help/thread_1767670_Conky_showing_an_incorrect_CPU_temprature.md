---
title: "Conky showing an incorrect CPU temprature"
date: 2011-05-26
forum: General Help
---

### Post by SuperUserDO on 2011-05-26
In .conkyrc i am using ```
 ${hwmon temp 1} °C
``` to show cpu temp but this temp is different from the temp in system monitor indicator which i think is the correct one...so what is the proper code to use in conky to show a proper cpu tem? Thank You.
Sensors detect:
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 11h thermal sensors...                           No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

---

### Post by timgood on 2011-05-26
Run ```
sensors
``` and the output will show you all the temperatures it can find. Then simply use the relevant temperature in your .conkyrc

Hope this helps.

---

### Post by SuperUserDO on 2011-05-26
Here is the output:
```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +25.6°C  (high = +70.0°C, crit = +99.5°C)  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +1.06 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.36 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +5.08 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +11.88 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    1824 RPM  (min =  200 RPM)
CHASSIS FAN Speed:2295 RPM  (min =  200 RPM)
CPU Temperature:   +38.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +34.0°C  (high = +45.0°C, crit = +75.0°C)  


```now it is clear that the conky shows temp1 not cpu temperature,how can i use it in conkyrc?

---

### Post by timgood on 2011-05-26
Something like:   ```
sensors atk0110-acpi-0 | grep CPU\ Temperature:\ | cut -c 22-60 
```# 22-60 adjust this range to something sensible for your machine.

Edit: changed sensor to the one shown in the output above.

---

### Post by timgood on 2011-05-26
Sorry, changed the sensor to the one shown in your output, edited above.

---

### Post by SuperUserDO on 2011-05-27
Thank you...it has already worked :)

---

