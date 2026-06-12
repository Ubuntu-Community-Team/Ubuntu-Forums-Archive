---
title: "Can't read/view/check the CPU Temp on Lenovo Laptop"
date: 2012-09-25
forum: General Help
---

### Post by amjjawad on 2012-09-25
Hi,

Lenovo G570, Core i5 2nd generation with 4GB RAM and Intel Graphics Card.

I have Lubuntu 12.04 x86_64 with 3.2.0-31-generic Kernel.

I have this installed: [http://www.upubuntu.com/2012/07/conky-2-nice-conky-desklet-for-your.html](http://www.upubuntu.com/2012/07/conky-2-nice-conky-desklet-for-your.html)

I have Jupiter 0.1.6 installed

I have Psensor installed

Each one of these are able to read the CPU Temperature and I'm 100% positive as I do have the same on the other machine and all work perfectly. The other machine is HP Pavilion DV6.
On this Lenovo, it doesn't work and it is driving me crazy.

Suddenly, all the laptops here have problems. I'm using 3 and all have problems from different kinds. What a coincidence!

Thanks!

---

### Post by marinara on 2012-09-26
have you tried sensors-detect

---

### Post by amjjawad on 2012-09-30
> **marinara said:**
> have you tried sensors-detect
I have and nothing changed at all.

Anyone here knows what is going on?
Why it works "OUT OF THE BOX" on all the other machines that I have around here and it is NOT working here on this Laptop?

Thanks in advance!

---

### Post by stinkeye on 2012-09-30
What does the command
```
**sensors**
```
give you.

eg my output...
```
[COLOR="Olive"]glen@Quantal:~$[/COLOR] **sensors**
it8720-isa-0228
Adapter: ISA adapter
in0:          +1.06 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.92 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
+5V:          +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +1.10 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +3.38 V  (min =  +0.00 V, max =  +4.08 V)
5VSB:         +3.02 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.25 V  
fan1:        2170 RPM  (min =    0 RPM)
fan2:           0 RPM  (min =    0 RPM)
fan3:        1119 RPM  (min =    0 RPM)
fan5:           0 RPM  (min =    0 RPM)
temp1:        +33.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +44.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +81.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:    +1.250 V
intrusion0:  ALARM

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +38.8°C  (high = +70.0°C)
                       (crit = +72.0°C, hyst = +70.0°C)
```

---

### Post by amjjawad on 2012-09-30
> **stinkeye said:**
> What does the command
```
**sensors**
```
give you.

Thanks for your reply.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:         +0.0°C  (crit = +127.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +50.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +48.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +46.0°C  (high = +86.0°C, crit = +100.0°C)
```

This machine is driving me crazy. I didn't install anything extra on the other machines and the temp works just fine. Why it is not on this? I don't really know. The installation is Fresh New and there is surely and absolutely no need to re-install. There must be something wrong somewhere??!!

---

### Post by stinkeye on 2012-09-30
psensors should show similar to sensors.
Is the problem no temp in conky or no temps at all.

Possibly run ```
sudo sensors-detect
``` again, making sure your answering yes to all. A couple of the questions default to "No".

---

### Post by amjjawad on 2012-09-30
> **stinkeye said:**
> Is the problem no temp in conky or no temps at all.
The answer is on Post #1 :)

> Possibly run ```
sudo sensors-detect
``` again, making sure your answering yes to all. A couple of the questions default to "No".

I already did as suggested on post #2 and I answered on post #3 :)

---

### Post by stinkeye on 2012-09-30
I know some conkys use $acpitemp.
Why it's not working on that laptop, noidea.

As the command sensors is giving you temps, you could change the $acpitemp (if used)
section in conky to use
```
${execpi 3 sensors | grep Physical | awk '{print $4}' | cut -c2-3}
```

Test in terminal to see what you get...
```
sensors | grep Physical | awk '{print $4}' | cut -c2-3
```

---

