---
title: "sensors not showing the full details?"
date: 2012-03-17
forum: General Help
---

### Post by senartcon on 2012-03-17
Hello,

I am not sure if my "sensors" report is complete. From all the websites i browsed, i saw "core temperatures" in every reports that people have got. But that is missing in mine.
```
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.04 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:      +3.26 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:        +4.92 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:      +12.04 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:     1638 RPM  (min =  600 RPM)
CHASSIS FAN Speed:    0 RPM  (min =  600 RPM)
POWER FAN Speed:   1391 RPM  (min =  600 RPM)
CPU Temperature:    +32.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:     +36.0°C  (high = +45.0°C, crit = +95.0°C)

```i also did "sensors-detect" which gave at the end,
```
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 
Driver `it87':
  * ISA bus, address 0x290
    Chip `ITE IT8712F Super IO Sensors' (confidence: 9)
```I found from the wiki page of lm_sensors that there should be something like 
```
Driver 'coretemp'
```which is not there.

Can someone help me fixing this?

And in my "hardinfo" (System profiler and Benchmark) nothing is displayed in the sensors. Could this be related to the above anomaly?

i am using Ubuntu 11.10

Thanks for any help

anand

---

### Post by ajgreeny on 2012-03-17
It is all very dependent upon your hardware.  I have tried on my system many times with different versions of Ubuntu and never get any output of any kind when I install lm-sensors and then run it.

Motherboard: ASUS - A7N8X-X
cpu: AMD - Sempron 2400+
BIOS: Phoenix Technologies, LTD
          ASUS A7N8X-X ACPI BIOS Rev 1011 (08/04/2004)

---

### Post by senartcon on 2012-03-17
My mother board is 
 M452-6224 : MSI 990FXA-GD65 AMD 9 Series AM3+

does this motherboard allows sensor detection?

---

### Post by Bobhuber on 2012-03-17
> **senartcon said:**
> My mother board is 
 M452-6224 : MSI 990FXA-GD65 AMD 9 Series AM3+

does this motherboard allows sensor detection?
Your sensors report is exceptional . The CPU temp is your core0 temp .Sensors detect will pick up all that is available and inform you if you (or it) needs to load more modules.
You have all the info you need plus some that you could remove if you wanted to.

---

### Post by Mark Phelps on 2012-03-18
I have the same problem -- the "fix" is to add the acpi_enforce_resources line to the kernel boot line.

Details are provided below:

[http://hydra.geht.net/tino/howto/linux/fixes/w83627hf/]("http://hydra.geht.net/tino/howto/linux/fixes/w83627hf/")

---

### Post by senartcon on 2012-03-18
> **Bobhuber said:**
> Your sensors report is exceptional . The CPU temp is your core0 temp .Sensors detect will pick up all that is available and inform you if you (or it) needs to load more modules.
You have all the info you need plus some that you could remove if you wanted to.

Acutally i have 4 cores.. thats why i doubt the report

---

### Post by senartcon on 2012-03-18
Thank you Mark for the link, i will try it and say__[]("http://ubuntuforums.org/member.php?u=311399").

---

### Post by senartcon on 2012-03-18
> **Mark Phelps said:**
> I have the same problem -- the "fix" is to add the acpi_enforce_resources line to the kernel boot line.

Details are provided below:

[http://hydra.geht.net/tino/howto/linux/fixes/w83627hf/](http://hydra.geht.net/tino/howto/linux/fixes/w83627hf/)


After doing the modifications mentioned in the above link i got the following, but i couldnt appreciate how better is this than my previous report, except for the more voltages listed!

```
$ sensors
it8712-isa-0290
Adapter: ISA adapter
in0:          +1.38 V  (min =  +0.77 V, max =  +0.11 V)  ALARM
in1:          +0.13 V  (min =  +0.13 V, max =  +2.56 V)  ALARM
in2:          +3.25 V  (min =  +1.04 V, max =  +1.54 V)  ALARM
+5V:          +0.38 V  (min =  +0.26 V, max =  +1.02 V)
in4:          +3.17 V  (min =  +0.54 V, max =  +0.00 V)  ALARM
in5:          +1.54 V  (min =  +0.03 V, max =  +1.02 V)  ALARM
in6:          +0.51 V  (min =  +1.31 V, max =  +2.06 V)  ALARM
5VSB:         +2.46 V  (min =  +0.10 V, max =  +1.34 V)  ALARM
Vbat:         +3.39 V  
fan1:        1687 RPM  (min = 1662 RPM)  ALARM
fan2:           0 RPM  (min = 1298 RPM)  ALARM
fan3:        1391 RPM  (min = 1140 RPM)
temp1:        +35.0°C  (low  = -120.0°C, high = +11.0°C)  sensor = thermistor
temp2:        +36.0°C  (low  =  +0.0°C, high =  +0.0°C)  sensor = thermistor
temp3:       -128.0°C  (low  = +48.0°C, high =  +0.0°C)  sensor = disabled
cpu0_vid:    +0.763 V

```

---

### Post by Bobhuber on 2012-03-18
> **senartcon said:**
> Acutally i have 4 cores.. thats why i doubt the report
So you think there is a difference in core temps ? Just what are you concerned with ? 
The CPU temp you posted is about right for an AMD quad core. Your MB temp also looks about right. If you do a bit of reading you will find that lm-sensors is by no means an exact tool and will not report the same on different chipsets and not at all on some as stated. It is meant to help you monitor correct ranges for your system. Unless you know exactly what you are doing and what the end result will be I would NOT recommend making changes to the grub config file as shown on that link.
Take a look at your /etc/sensors3.config file and you will get a bit of an idea of what can be changed in what you see when you run the sensors command. Heres a picture of my readout for an overclocked  quad core AMD which is very close to what it should be with adequate cooling.

---

### Post by senartcon on 2012-03-19
> **Bobhuber said:**
> So you think there is a difference in core temps ? Just what are you concerned with ? 
The CPU temp you posted is about right for an AMD quad core. Your MB temp also looks about right. If you do a bit of reading you will find that lm-sensors is by no means an exact tool and will not report the same on different chipsets and not at all on some as stated. It is meant to help you monitor correct ranges for your system. Unless you know exactly what you are doing and what the end result will be I would NOT recommend making changes to the grub config file as shown on that link.
Take a look at your /etc/sensors3.config file and you will get a bit of an idea of what can be changed in what you see when you run the sensors command. Heres a picture of my readout for an overclocked  quad core AMD which is very close to what it should be with adequate cooling.

Ok, i will take your suggestion. Thanks

---

### Post by Mark Phelps on 2012-03-19
> **senartcon said:**
> After doing the modifications mentioned in the above link i got the following, but i couldnt appreciate how better is this than my previous report, except for the more voltages listed!

Sorry, didn't understand that what you wanted was the temp of each of the cores!

I have a six-core AMD processor, and in both Linux and Windows, only get one core temp reported.  Get usage for all six cores, but not individual temps.

Don't even know if that is possible.

---

