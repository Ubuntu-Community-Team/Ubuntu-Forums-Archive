---
title: "GKrellM not sensing Voltage/Fan Sensors"
date: 2011-01-13
forum: General Help
---

### Post by ozark_hillbilly on 2011-01-13
GKrellM worked fine under 9.04.

W/ 10.04 it works but does not sense the Fan or Voltage sensors.

I transplanted the old folder over to /home after downloading GKrellM, hddtemp, and lm-sensors thru Synaptic.

Ran the hddtemp and lm sensors in terminal w/ no problems.
Running sensors revealed all inputs: cpu temps, fan speeds, and
mobo voltages.

GKrellM downloaded was ver 2.3.4 while my old folder data was 2.3.2. Sensor config file is same format just that the old config file has all the voltage/fan pointers assigned as well.

Weird thing is that GKrellM will overwrite the sensor-config file (that has ALL the sensor defined inputs pasted into it) after going into the program and selecting Configuration. It reverts to the sensor-config file created after running lm-sensors and hddtemp under 10.04. So it's autowriting itself and not picking up the fan/voltage inputs.

Displaying the data thru the Sensor Applet in the Desktop panel is OK but I prefer having everything on GKrellM. It's a much cleaner, easy to view system. 

Anybody got a clue why GKrellM is overwriting the sensor-config file. That should be static, unlike the user-config file.

---

### Post by ozark_hillbilly on 2011-01-15
Bump...

---

### Post by rrrrrichard on 2011-05-23
Still fails in 11.04.  A fix would be much appreciated.

---

### Post by P . P . L . on 2011-05-27
Hi.

I've got the same problem with 10.04lts, NO volts, NO fans, NO M/B temp i can get core temps, it's an intel quad & i also get H/Drive temp & Graphics card temp.

Everything worked fine with 8.04lts but that has run out of service time so i had to upgrade, not good that it doesn't work now.

--------------------------------------------------------------------------------------------------------------------------------

Edit// Funny how sensors applet has no trouble showing everything, pity that it takes up so much space to show all the readings.

---

### Post by Malibyte on 2011-07-06
Same problem here...ASUS p5K deluxe with Q6600...anyone figured it out?  Gkrellm can't display the fan speeds and voltages but has no problems with anything else (individual core temps but not the composite one), HDD temps, etc.  The sensors cli prog works fine:

[rcs@vader: ~]$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.13 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.23 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +4.99 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.04 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     2280 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:3245 RPM  (min =  600 RPM)
CHASSIS2 FAN Speed:3125 RPM  (min =  600 RPM)
CHASSIS3 FAN Speed:1687 RPM  (min =  800 RPM)
CPU Temperature:    +45.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:     +44.0°C  (high = +45.0°C, crit = +95.0°C)  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +59.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +60.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +56.0°C  (high = +84.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +58.0°C  (high = +84.0°C, crit = +100.0°C)

---

### Post by Mark Phelps on 2011-07-06
The PROBLEM is Canonical, not gkrellm.  The version obtained from the repos continues to be compiled WITHOUT the necessary libraries (libsensors) to allow it to read some sensors.

The link below is to a bug report that explains this:

[https://bugs.launchpad.net/ubuntu/+source/gkrellm/+bug/688944]("https://bugs.launchpad.net/ubuntu/+source/gkrellm/+bug/688944")

So basically, you have to obtain the source and compile it yourself WITH libsensors support builit in.  THEN, it will read the latest sensors and display the information.

---

### Post by Malibyte on 2011-07-10
Thanks.  Their not having compiled in lm-sensors support makes no damn sense.  OK, I guess I'll have to compile from source if I really want it that bad...however, I'll have to install about 25 dependent packages to compile this thing.  Crap.

---

