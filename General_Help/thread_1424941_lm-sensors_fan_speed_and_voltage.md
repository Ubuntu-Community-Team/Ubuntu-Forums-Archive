---
title: "lm-sensors fan speed and voltage"
date: 2010-03-08
forum: General Help
---

### Post by ancleessen4 on 2010-03-08
I am unable to get fan speeds (cpu and sys fan) and voltage readings from lm-sensors. I have followed the various threads here but no luck.
Here is what I can obtain from sensors detect;

```
neil@neil-ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +42.0°C  (crit = +80.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +42.0°C  (high = +78.0°C, crit = +100.0°C)  
```

Am I missing something here?
I am sure in the not too distant past I was able to pick up these readings from this motherboard.:confused:

---

### Post by Mr.Banana on 2010-03-08
Try restarting the computer. Every time I install lm sensors, If I dont reboot the system after installing lm-sensors I am only able to get the cpu and system temperatures, but after a reboot I have them all- cpu, cpu cores, hdd temps, voltages, fan speed. 

Hope this helps, and of course, this is just my system, your system might be way different.

---

### Post by ancleessen4 on 2010-03-08
I am afraid not Mr.Banana-a reboot did not give any further readings.
I suspect I am doing something fundamentally wrong as another machine with similar specs that I have, running Arch linux, has the same problem of only providing temps from lm-sensors...:confused::confused:

---

### Post by richardjh on 2010-03-08
Have you run sensors-detect? 
If you are sure this board has worked before this will get you well on your way. 

If sensors-detect doesn't find the chips onboard, there is the latest version on the lm-sensors.org site which is more up to date. 
It is just a perl script so you don't need to install anything. Just run it.

That should tell you what chips are on the board and what kernel modules should be loaded to get them recognised.

Once all the kernel modules are loaded, you need to set up your sensors.conf file for those chips. You may be lucky and find a configuration on lm-sensors.org otherwise you need to search about a bit online.

Then it should all work. You then need to add the modprobe commands to /etc/rc.local so they persist over reboots.

If you still can't get the sensors working after a quick try, then post back with the summary at the end of the sensors-detect output along with the description of the motherboard.

---

### Post by doas777 on 2010-03-08
for the most part lm-sensors/sensors-applet do what I need them too, but they never expose all the sensors i need. out of at least 15 boxes, i've only ever seen it actually get fan speeds on one of them. sensors are just not standardized enough.

---

### Post by ancleessen4 on 2010-03-08
Thank you richardjh.
Yes, I did run sensors-detect.
I will give the latest 'sensors-detect' version a run (after my night shift :-({|=)
I will give you an update later.

---

### Post by ancleessen4 on 2010-03-09
Solved!
This was solved for me by following this [wiki]("http://wiki.archlinux.org/index.php/Lm_sensors#Notice_for_kernels_.3E.3D2.6.31") guide on the Arch linux forums. 
Notice for kernels  >=2.6.31
Added ```
acpi_enforce_resources=lax
``` to /boot/grub/menu.lst and re-booted.

Et voila!

```
/ You are going to have a new love \
\ affair.                          /
 ----------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
neil@neil-ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +80.0°C)                  

w83627dhg-isa-0290
Adapter: ISA adapter
Vcore:       +1.13 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +0.91 V  (min =  +1.04 V, max =  +0.71 V)   ALARM
AVCC:        +3.30 V  (min =  +2.98 V, max =  +3.63 V)   
VCC:         +3.30 V  (min =  +2.98 V, max =  +3.63 V)   
in4:         +1.10 V  (min =  +0.01 V, max =  +0.50 V)   ALARM
in5:         +1.19 V  (min =  +0.70 V, max =  +1.30 V)   
in6:         +1.55 V  (min =  +0.00 V, max =  +1.14 V)   ALARM
3VSB:        +3.25 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:        +3.02 V  (min =  +2.70 V, max =  +3.30 V)   
fan1:        598 RPM  (min =  332 RPM, div = 16)
fan2:        878 RPM  (min =  332 RPM, div = 16)
fan3:          0 RPM  (min =  340 RPM, div = 128)  ALARM
fan4:          0 RPM  (min =  340 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 2636 RPM, div = 128)  ALARM
temp1:       +29.0°C  (high = +56.0°C, hyst =  +0.0°C)  sensor = thermistor
temp2:       +40.0°C  (high = +70.0°C, hyst = +65.0°C)  sensor = diode
temp3:       +39.0°C  (high = +70.0°C, hyst = +65.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +42.0°C  (high = +78.0°C, crit = +100.0°C)  


```
:guitar:

---

### Post by richardjh on 2010-03-09
You have some spare time on the night shift? :)

---

### Post by doas777 on 2010-03-09
so where would you put that menu.lst line in a grub2 system like karmic or lucid?

---

### Post by donfilipo on 2010-04-13
> **ancleessen4 said:**
> Solved!
This was solved for me by following this [wiki]("http://wiki.archlinux.org/index.php/Lm_sensors#Notice_for_kernels_.3E.3D2.6.31") guide on the Arch linux forums. 
Notice for kernels  >=2.6.31
Added ```
acpi_enforce_resources=lax
``` to /boot/grub/menu.lst and re-booted.

Et voila!

```
/ You are going to have a new love \
\ affair.                          /
 ----------------------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
neil@neil-ubuntu:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +80.0°C)                  

w83627dhg-isa-0290
Adapter: ISA adapter
Vcore:       +1.13 V  (min =  +0.00 V, max =  +1.74 V)   
in1:         +0.91 V  (min =  +1.04 V, max =  +0.71 V)   ALARM
AVCC:        +3.30 V  (min =  +2.98 V, max =  +3.63 V)   
VCC:         +3.30 V  (min =  +2.98 V, max =  +3.63 V)   
in4:         +1.10 V  (min =  +0.01 V, max =  +0.50 V)   ALARM
in5:         +1.19 V  (min =  +0.70 V, max =  +1.30 V)   
in6:         +1.55 V  (min =  +0.00 V, max =  +1.14 V)   ALARM
3VSB:        +3.25 V  (min =  +2.98 V, max =  +3.63 V)   
Vbat:        +3.02 V  (min =  +2.70 V, max =  +3.30 V)   
fan1:        598 RPM  (min =  332 RPM, div = 16)
fan2:        878 RPM  (min =  332 RPM, div = 16)
fan3:          0 RPM  (min =  340 RPM, div = 128)  ALARM
fan4:          0 RPM  (min =  340 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 2636 RPM, div = 128)  ALARM
temp1:       +29.0°C  (high = +56.0°C, hyst =  +0.0°C)  sensor = thermistor
temp2:       +40.0°C  (high = +70.0°C, hyst = +65.0°C)  sensor = diode
temp3:       +39.0°C  (high = +70.0°C, hyst = +65.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +42.0°C  (high = +78.0°C, crit = +100.0°C)  


```
:guitar:

Sounds nice, because it's really annoying to hear your own machine suffering:) But when I tried it.... no go:( I have no /boot/grub/menu.lst

only /boot/grub/
Ubuntu is installed via wubi exe on second partition and first OS is Windoz 7:)
Any idea?

---

