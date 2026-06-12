---
title: "How to lower CPU fan speed?"
date: 2010-05-31
forum: General Help
---

### Post by rizzeh on 2010-05-31
I'm trying to lower RPM of CPU and Chassis fans when under low load, it's much too loud. i have sensors installed, output below. Also gnome applet shows all speeds correct if somewhat too high - i have zalman cooler that should be comfortable at 800rpm or lower but it doesnt go below 1400rpm. How can i set lower speed for CPU cooler fan? 

```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +75.0°C)                  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:          +1.35 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:          +3.40 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:          +5.13 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:         +12.43 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:         1500 RPM  (min =    0 RPM)
CHASSIS FAN Speed:     1603 RPM  (min =    0 RPM)
POWER FAN Speed:          0 RPM  (min =    0 RPM)
CHASSIS4 FAN FAN Speed:   0 RPM  (min =    0 RPM)
CHASSIS2 FAN FAN Speed:   0 RPM  (min =    0 RPM)
CHASSIS3 FAN FAN Speed:1051 RPM  (min =    0 RPM)
CPU Temperature:        +37.0°C  (high = +90.0°C, crit = +125.0°C)  
MB Temperature:         +42.0°C  (high = +45.0°C, crit = +90.0°C)  

```

---

### Post by davidmohammed on 2010-05-31
acpi issues are usually down to bios issues - most manufacturers concentrate on windows drivers and ignore linux...

usual suggestions - update your bios to the latest.

investigate booting with noapic, nolapic in your grub.

investigate booting with acpi_os= values in your grub... with examples such as in this [thread]("http://ubuntuforums.org/showthread.php?t=1497866")

---

### Post by rizzeh on 2010-05-31
Thanks, something to work on :)
Trying to avoid pluging in manual speed controller to the pc case, way too many wires as it is.

---

### Post by Mark Phelps on 2010-05-31
Have you thought about the fact that fan speeds are often the result of heat generation; meaning, if your fans are running fast, it's because the hardware is running hot.

If you artificially lower the fan speed just to reduce the sound, you will almost certainly burn out the device the fan is cooling.

The more important question is WHY the fans are running so much.

It's more important to solve the overheating problem than to just slow down the fans.

---

