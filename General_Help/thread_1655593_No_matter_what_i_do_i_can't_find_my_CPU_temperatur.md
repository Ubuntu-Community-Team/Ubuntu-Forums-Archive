---
title: "No matter what i do i can't find my CPU temperature!"
date: 2010-12-29
forum: General Help
---

### Post by ~Middle on 2010-12-29
I have tried lm-sensors and a few others, firefox just crashed so i cant be btoerheed to write out my very large post again sorry.

Phenom II X6 1090T
MSI-890FXA-GD70 motherboard
Ubuntu 10.10

Senors:

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +0.0°C  (high = +70.0°C)   

sensors-detect

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK


Any ideas?

P.S. There is a debugging panel on my motherboard, and i think that that displays the CPU temperature, although i am not sure.

Thanks a lot

---

### Post by dcstar on 2010-12-30
> **~Middle said:**
> I have tried lm-sensors and a few others, firefox just crashed so i cant be btoerheed to write out my very large post again sorry.

Phenom II X6 1090T
**MSI-890FXA-GD70 motherboard**
........

lm-sensors version 3.2.0 supports the Fintek F71889ED chipset on that MB:

[http://www.lm-sensors.org/browser/lm-sensors/tags/V3-2-0/CHANGES](http://www.lm-sensors.org/browser/lm-sensors/tags/V3-2-0/CHANGES)

[http://www.lm-sensors.org/wiki/Download](http://www.lm-sensors.org/wiki/Download)

---

### Post by ~Middle on 2010-12-30
So if i apt-get lm-sensors, it will not be the latest version?

I tried installing it but i am not sure as to how it went, is there any way to check?

---

### Post by IWantFroyo on 2010-12-30
Have you looked in BIOS? Also, it sometimes shows stuff like CPU temperature and fan rpm during bootup (before it goes into Ubuntu).

---

### Post by ~Middle on 2010-12-30
Yeah there are CPU and system temperatures, and there are fan speeds etc..

But it isn't much good in the bios....

---

### Post by Frogs Hair on 2010-12-30
After installing lm-sensors you can install sensors-applet , which can be placed on the Gnome panel from the add to panel menu . This link has some useful terminal commands . [http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

---

### Post by ~Middle on 2010-12-30
When i run sensors this is all the out put i get:


k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +15.5°C  (high = +70.0°C)                  

What is this the tempreature of?

---

