---
title: "hwmon0 and hwmon1 switch at boot"
date: 2010-10-31
forum: General Help
---

### Post by slamhound on 2010-10-31
I use conky to display cpu temperature and fan speed.  This all worked perfectly on 10.04, but with the upgrade to 10.10, I've been having some problems with this.  Conky reads from hwmon to get this info, but hwmon0 and hwmon1 often switch at boot, so the specifications in .conkyrc are often wrong (which causes Conky to fail to load).  I've googled this, and the limited hits I've found propose solutions that don't seem ideal (the solution in this [link]("http://ubuntuforums.org/showpost.php?p=9636358&postcount=2") is advised against elsewhere), or they propose solutions that don't seem to apply to Ubuntu (i.e., they are arch-specific).  Any thoughts on how to make sure that hwmon0 and hwmon1 stay the same at each boot?  Here is my output from "sensors":

```
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.06 V  (min =  +0.85 V, max =  +1.70 V)
 +3.3 Voltage:       +3.52 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +4.97 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.82 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      2311 RPM  (min =  600 RPM)
CHASSIS FAN Speed:     0 RPM  (min =  600 RPM)
CHASSIS FAN 2 Speed:   0 RPM  (min =  600 RPM)
CPU Temperature:     +36.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:      +35.0°C  (high = +45.0°C, crit = +75.0°C)  

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +27.1°C  (high = +70.0°C, crit = +90.0°C) 
```

I want Conky to read from the atk0110-acpi-0 output, but sometimes that is listed first, sometimes second.

---

### Post by slamhound on 2011-02-28
All these months later, finally found a solution:  just blacklist k10temp in /etc/modprobe.d/blacklist.conf.  Now only one of these modules loads, which means that the temperatures are always found in hwmon0.

---

### Post by Cypher2 on 2011-04-17
I confirm the blacklisting worked for me.. everything goes to hwmon0 now, except for my nvidia card which stays on hwmon1 :)

Thank you so very much for this!

---

