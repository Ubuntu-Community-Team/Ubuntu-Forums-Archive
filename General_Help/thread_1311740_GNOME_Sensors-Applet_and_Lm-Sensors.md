---
title: "GNOME Sensors-Applet and Lm-Sensors"
date: 2009-11-02
forum: General Help
---

### Post by jnew93 on 2009-11-02
Ok, so today I installed lm-sensors 3.1.1 from source in order to take advantage of the atk0110 ACPI driver. I had always run the it87 module to monitor my temps, however with kernel release 2.6.31 that module has been disabled for stability reasons (I have been told that is why it stopped working). Now, when I run sensors in terminal I get:

```

john@Mitsune:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:     +0.96 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:     +3.33 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:       +4.97 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:     +12.04 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:    2616 RPM  (min =  600 RPM)
CHASSIS FAN Speed:1211 RPM  (min =  600 RPM)
POWER FAN Speed:     0 RPM  (min =  600 RPM)
CPU Temperature:   +31.0°C  (high = +60.0°C, crit = +95.0°C)  
MB Temperature:    +27.0°C  (high = +45.0°C, crit = +95.0°C)  

```

All well and good. My problem lies with gnome sensors-applet. It will not read the sensors! I only see a "No Sensors Detected" message when I load the applet. The website for the applet claims support for ACPI, and the required options (CONFIG_ACPI & CONFIG_ACPI_THERMAL) are set to yes in my boot configuration file. 

What I want to know is, why is this happening? Thanks in advance for any help! :D

---

### Post by jnew93 on 2009-11-02
Also, other similar sensor applets seem to have the same problem...

---

### Post by spmurphy on 2009-12-31
I also have a working ACPI atk0110 but the sensor applet doesn't pick it up.

I have a working hard disk temp sensor and nvidia sensors, just the ACPI that doesn't work.

I had it working on 9.04, I'm sure. This is a clean install of 9.10 though and it doesn't work. The "sensors" command shows all the readings from the BIOS (fans, voltages, temperatures etc.) but they're not shown in the gnome panel applet.

Does anyone know how to fix this? I can't remember what I twiddled to make it work in 9.04.

Where did the services application go too? That seems to have disappeared.

```
atk0110-acpi-0
Adapter: ACPI interface
 +3.3 Voltage:            +3.33 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:              +5.09 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:            +12.31 V  (min = +10.20 V, max = +13.80 V)
DRAM Voltage:             +1.65 V  (min =  +1.40 V, max =  +1.90 V)
CPU Vcore Voltage:        +0.86 V  (min =  +0.80 V, max =  +2.50 V)
CPU PLL Voltage:          +1.79 V  (min =  +1.20 V, max =  +3.01 V)
VTT CPU Voltage:          +1.36 V  (min =  +0.80 V, max =  +2.00 V)
DRAM Voltage:             +1.06 V  (min =  +1.00 V, max =  +1.30 V)
DRAM Voltage:             +1.50 V  (min =  +1.80 V, max =  +3.40 V)
DRAM Voltage:             +1.80 V  (min =  +1.80 V, max =  +3.40 V)
DRAM Termination Voltage: +0.81 V  (min =  +0.60 V, max =  +1.30 V)
CPU FAN Speed:              0 RPM  (min =  600 RPM)
CHA_FAN1 Speed:             0 RPM  (min =  600 RPM)
CHA_FAN2 Speed:             0 RPM  (min =  600 RPM)
CHA_FAN3 Speed:             0 RPM  (min =  600 RPM)
PWR_FAN Speed:            677 RPM  (min =  600 RPM)
OPT_FAN1 Speed:             0 RPM  (min =  600 RPM)
OPT_FAN2 Speed:             0 RPM  (min =  600 RPM)
OPT_FAN3 Speed:             0 RPM  (min =  600 RPM)
CPU Temperature:          +34.5°C  (high = +60.0°C, crit = +65.0°C)  
MB Temperature:           +41.0°C  (high = +45.0°C, crit = +55.0°C)  
PCH Temperature:          +32.0°C  (high = +65.0°C, crit = +95.0°C)  
POWER Temperature:        +32.0°C  (high = +55.0°C, crit = +95.0°C)  
OPT_TEMP1 Temperature:     +0.0°C  (high = +45.0°C, crit = +45.0°C)  
OPT_TEMP2 Temperature:     +0.0°C  (high = +45.0°C, crit = +45.0°C)  
OPT_TEMP3 Temperature:     +0.0°C  (high = +45.0°C, crit = +45.0°C)  

```

Interestingly "sensors" doesn't show the nvidia and hard disk sensors; the applet shows those but not the atk0110.

---

### Post by spmurphy on 2010-01-01
I've just rebuilt the sensor applet from source so it's the latest version and still no luck.

Currently sensors 3.1.1 and gnome sensors applet 2.2.5.

sensors still works, sensors applet still only show nvidia and hddtemp.

---

### Post by spmurphy on 2010-01-01
fixed

checked out trunk of lm_sensors, rebuilt

replaced libsensors in /usr/lib with newly built ones

reboot

panel applet now works \o/

---

