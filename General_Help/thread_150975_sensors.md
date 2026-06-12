---
title: "sensors"
date: 2006-03-27
forum: General Help
---

### Post by mitjab on 2006-03-27
why sensor aplet show me only one 1 senso

if i try sensors in console works fine

sensors
w83627hf-isa-0290
Adapter: ISA adapter
VCore 1:   +1.62 V  (min =  +0.00 V, max =  +0.00 V)
VCore 2:   +1.60 V  (min =  +0.00 V, max =  +0.00 V)
+3.3V:     +2.74 V  (min =  +3.14 V, max =  +3.47 V)
+5V:       +5.03 V  (min =  +4.76 V, max =  +5.24 V)
+12V:     +11.98 V  (min = +10.82 V, max = +13.19 V)
-12V:      -7.10 V  (min = -13.18 V, max = -10.80 V)
-5V:       -5.10 V  (min =  -5.25 V, max =  -4.75 V)
V5SB:      +5.48 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +2.93 V  (min =  +2.40 V, max =  +3.60 V)
fan1:        0 RPM  (min =   -1 RPM, div = 2)
fan2:        0 RPM  (min =   -1 RPM, div = 2)
fan3:     2556 RPM  (min = 21093 RPM, div = 8)
temp1:        +8°C  (high =  -120°C, hyst =  -125°C)   sensor = thermistor 
temp2:     +45.0°C  (high =   +65°C, hyst =   +60°C)   sensor = thermistor 
temp3:     +32.5°C  (high =   +65°C, hyst =   +60°C)   sensor = thermistor 
vid:      +0.000 V  (VRM Version 9.0)
alarms:
beep_enable:
          Sound alarm disabled

eeprom-i2c-0-51
Adapter: SMBus nForce2 adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

eeprom-i2c-0-50
Adapter: SMBus nForce2 adapter at 5000
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

mitjab@ubuntu:~$

how to enable sound alarm

alarms:
beep_enable:
Sound alarm disabled


is there any better program then sensor-aplet that wil show temp of vcore,...
ksensor not working in gnome!

---

### Post by dcstar on 2006-03-27
[QUOTE=mitjab]
......
is there any better program then sensor-aplet that wil show temp of vcore,...
ksensor not working in gnome![/QUOTE]
gkrellm, xsensors

---

### Post by taurus on 2006-03-27
You need to look into /etc/sensors.conf.

---

