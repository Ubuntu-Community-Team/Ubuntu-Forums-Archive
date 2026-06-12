---
title: "lm-sensors acpitz-virtual-0 Adapter: Virtual device temp1:   &lt;- What is it?"
date: 2009-08-23
forum: General Help
---

### Post by Maintech on 2009-08-23
I have spent considerable hours searching forums and googling. I have yet to find out what "lm-sensors acpitz-virtual-0 Adapter: Virtual device temp1:" is actually looking at. I have an Abit IP35 motherboard with Ubuntu 9.04 installed. Here is the output from sensors:

> [B]acpitz-virtual-0
Adapter: Virtual device
temp1: +47.0°C (crit = +90.0°C) <--- Keeps overheating to 121 C and shutting the computer down.

w83627dhg-isa-0290
Adapter: ISA adapter
VCore: +1.13 V (min = +0.00 V, max = +1.74 V)
in1: +6.34 V (min = +6.97 V, max = +3.38 V) ALARM 
AVCC: +3.26 V (min = +2.11 V, max = +0.58 V) ALARM <--My bios isn't set for this high voltage. Don't know why it is reading this high.
3VCC: +3.26 V (min = +1.97 V, max = +2.56 V) ALARM
in4: +1.19 V (min = +0.00 V, max = +0.51 V) ALARM
in5: +1.25 V (min = +1.22 V, max = +0.53 V) ALARM
in6: +5.07 V (min = +4.92 V, max = +0.46 V) ALARM
VSB: +3.22 V (min = +0.00 V, max = +0.53 V) ALARM
VBAT: +3.17 V (min = +0.30 V, max = +2.88 V) ALARM
Case Fan: 0 RPM (min = 340 RPM, div = 128) ALARM
CPU Fan: 1534 RPM (min = 332 RPM, div = 16)
Aux Fan: 0 RPM (min = 340 RPM, div = 128) ALARM
fan4: 0 RPM (min = 340 RPM, div = 128) ALARM
fan5: 0 RPM (min = 2109 RPM, div = 128) ALARM
Sys Temp: +40.0°C (high = +16.0°C, hyst = -124.0°C) ALARM sensor = thermistor
CPU Temp: +47.0°C (high = +80.0°C, hyst = +75.0°C) sensor = diode
AUX Temp: +42.0°C (high = +80.0°C, hyst = +75.0°C) sensor = thermistor
cpu0_vid: +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0: +42.0°C (high = +82.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1: +38.0°C (high = +82.0°C, crit = +100.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2: +44.0°C (high = +82.0°C, crit = +100.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3: +37.0°C (high = +82.0°C, crit = +100.0°C)[/B]

Virtual Device Temp 1 keeps going up to 121 degrees and the computer shuts down. None of the others overheat. Also, my bios does not show my voltages to be set like it lists above. The bios in the motherboard is the latest from Abit. Anyone have any ideas about what is going on???

---

### Post by Nicholasx on 2011-09-04
acpitz-virtual-0 adapter shows the temperature underneath a CPU base, as far as I know:)

---

