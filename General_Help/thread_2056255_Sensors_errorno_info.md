---
title: "Sensors error/no info"
date: 2012-09-11
forum: General Help
---

### Post by Trompette83 on 2012-09-11
Hi,

I want to display the sensors info for my new built.
Asrock 970 Extrem4, FX-8120, Ubuntu 12.04.

I installed
Hardware Sensors Indicator 0.2 with Indicator Applet 0.50
Psensor 0.6.2.16
lm-sensors
(I run them separately)

CLI lm-sensors install has been done with the commands 
> Install and Configure lm-sensors

    Install the lm-sensors package.

    Run sudo sensors-detect and answer YES to all YES/no questions.

    At the end of sensors-detect, a list of modules that needs to be loaded will displayed. Type "yes" to have sensors-detect insert those modules into /etc/modules.

    Next, run sudo service module-init-tools restart This will read the changes you made to /etc/modules in step 3, and insert the new modules into the kernel. 


CLI sensors says
> ~$ sensors
nct6776-isa-0290
Adapter: ISA adapter
Vcore:        +0.90 V  (min =  +0.00 V, max =  +1.74 V)
in1:          +1.85 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
AVCC:         +3.31 V  (min =  +2.98 V, max =  +3.63 V)
+3.3V:        +3.30 V  (min =  +2.98 V, max =  +3.63 V)
in4:          +0.03 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
in5:          +1.72 V  (min =  +0.00 V, max =  +0.00 V)  ALARM
3VSB:         +3.46 V  (min =  +2.98 V, max =  +3.63 V)
Vbat:         +3.34 V  (min =  +2.70 V, max =  +3.30 V)  ALARM
fan1:           0 RPM  (min =    0 RPM)  ALARM
**fan2:           0 RPM**  (min =    0 RPM)  ALARM
**fan3:           0 RPM**  (min =    0 RPM)  ALARM
fan4:           0 RPM  (min =    0 RPM)  ALARM
fan5:           0 RPM  (min =    0 RPM)  ALARM
SYSTIN:       +27.0°C  (high =  +0.0°C, hyst =  +0.0°C)  ALARM  sensor = thermistor
CPUTIN:       +24.5°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
**AUXTIN:      +127.5°C ** (high = +114.0°C, hyst = +114.0°C)  ALARM  sensor = thermistor
cpu0_vid:    +0.000 V
intrusion0:  ALARM
intrusion1:  OK

**k10temp-pci-00c3**
Adapter: PCI adapter
temp1:         **+5.5°C**  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +67.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       42.54 W  (crit = 124.95 W)



3 problems:
- k10temp-pci-00c3 should be the CPU has temp = +5.5°C while BIOS shows around 40°C.
- fan1-5 have no value while BIOS shows CPU fan and Chassis 2 and 3 values.
- What aer AUXTIN at 127.5°C and SYSTIN, CPUTIN in the motherboard?

The only correct value is GPU Temp = about 34°C confirmed by the NVidia driver.
The 2 other programs have the same results.

Do I need to run a stress program like CPUBURN to see whether the temp increase and become good?
Any idea how to get the right value?

Many thanks

---

### Post by mcduck on 2012-09-11
While some people might be really lucky and get correct values out-of-the-box with lm-sensors, in most cases you'll have to check yourself which value might be related to which sensor and then edit the /etc/sensors.conf file to set the min/max limits, and in some cases create formulas and mulitpliers for calculating the correct value from the raw value the motherboard's sensors are giving. The problem is that there isn't any common standard for the sensors, same sensor might be used for completely different purpose on a different motherboard model...

Usually the best approach is to run some resource-heavy program for a while and see how different values react to it. The temperatue that rises immediately would be the CPU core, quickly followeed by CPU socket sensor, then motherboad/chipset sensor. And the case/ambient temperature should pretty much stay the same, at least if you have any kind of decent case for your computer. Ambinet temperature should also be pretty close to the room temperature.

...and like you can see from the multiple alarms for things with min/max limits both at 0, you'll need to configure those yourself.

In the end you'll probably have some sensors that aren't doing anyhting at all, you can just disable those. Not every motherboard has all the sensors a certain sensor monitoring chip might support...

(I can't help you with the fan speeds, though, since you aren't getting any value for them there of course is no way to calculate the correct values...)

---

### Post by Trompette83 on 2012-09-11
Thank you mcduck.

I'll try to ask in the Asrock forum what are the sensors in this M/B and more details.
I am afraid it will be not easy.

Question:
Are the names of the sensors (nct6776-isa-0290, k10temp-pci-00c3...) and the names of the parameters (SYSTIN, CPUTIN ...) specific to the OS (Linux or Windows) or are they given by the motherboard?

---

### Post by mcduck on 2012-09-11
The sensor names are at least *related* to the names of the actual sensor chips and the busses they are connected to. So anybody familiar with the sensor implementation on thwe motherboard should know what the names are referring to.

As far as I know the names of the parameters are just names lm-sensors gives to different raw values it receives from the sensor chips. (of course many of the names are commonly used terms, but like I said the problem is that each value might not be connected to the sensor it should bve, as lm-sensors doesn't actally know what the values it receives really are, unless it happens to have a pre-made configuration for your specific motherboard model you might end with data from fan speed being mapped to CPU temperature, for example.

---

