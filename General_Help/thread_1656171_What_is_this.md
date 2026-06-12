---
title: "What is this?"
date: 2010-12-30
forum: General Help
---

### Post by ~Middle on 2010-12-30
I am trying to find out my CPU tempreature; so far if i run sensors i get this:
 
k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +15.5°C  (high = +70.0°C)                  

Now a few snippets from random forums have suggested that this is in fact the CPU temperature, and the other bit of evidence is that when i run 

stress -c 6 -t 30 

To stress test the CPU to try to increase its tempreature the tempreature rises:

k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +41.0°C  (high = +70.0°C)                  

However the argument against it being my CPU tempreature is that isn't 15 C a bit cool even for idle?

and 
[B]
k10temp-pci-00c3
Adapter: PCI adapter[/B]
temp1:       +41.0°C  (high = +70.0°C)    

Please help me!!!!

Cheers

---

### Post by daqron on 2010-12-30
> **~Middle said:**
> k10temp-pci-00c3
Adapter: PCI adapter
temp1:       +15.5°C  (high = +70.0°C)
Not an expert but was messing around with CPU temp measurement the other day so I'll share what I know. 

Sensors should output something like ```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +26.7°C  (crit = +112.0°C)                  
temp2:       +57.0°C  (crit = +112.0°C)                  
temp3:       +51.0°C  (crit = +90.0°C)                  
temp4:       +56.0°C  (crit = +107.0°C) 
```

I don't know why it's showing you info for a PCI adapter. Try following the lm-sensors how-to at [http://www.linuxappliancedesign.com/articles/sensors/sensors.html](http://www.linuxappliancedesign.com/articles/sensors/sensors.html). Short summary for the impatient ...
```
sudo apt-get install lm-sensors
sudo sensors-detect
```
Press return a bunch of times. Optionally, read what it says (haha, just kidding). Copy what's in between "#----cut here----" and "#----cut here----" (probably something like "[COLOR="Red"]coretemp[/COLOR]").

```
modprobe [COLOR="Red"]coretemp[/COLOR]
sensors
```

Hope that helps!

---

### Post by knutschr on 2010-12-30
Can anyone tell what the numbers behind temp mean?
```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +91.0°C  (crit = +98.0°C)                  
temp2:       +76.0°C  (crit = +98.0°C) 
```

---

### Post by daqron on 2010-12-30
> **knutschr said:**
> Can anyone tell what the numbers behind temp mean?
```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +91.0°C  (crit = +98.0°C)                  
temp2:       +76.0°C  (crit = +98.0°C) 
```
Multi-processor systems report different temps for each processor. Also, multi-core CPUs report temps individually for each core.

---

### Post by ~Middle on 2010-12-30
Yeah i did the whole lm-sensors sensor detect thing, and it only detect that sensor, whcih is fine, but i really want to know what the hell it is!

Someone must know!

Cheers

---

### Post by daqron on 2010-12-30
> **~Middle said:**
> Yeah i did the whole lm-sensors sensor detect thing, and it only detect that sensor, whcih is fine, but i really want to know what the hell it is!
Is there anything in /proc/acpi/thermal_zone/ ? If there's a CPU directory in there you could do ```
cat /proc/acpi/thermal_zone/[COLOR="Red"]CPU_DIRECTORY_NAME[/COLOR]/temperature
``` and compare that to your output from sensors. The directory name isn't standard across vendors. Mine is "CPUZ".

---

### Post by ~Middle on 2010-12-30
Doesn't look like it =[

middle@The-Beast:~$ cd /proc/acpi/thermal_zone/
middle@The-Beast:/proc/acpi/thermal_zone$ ls
middle@The-Beast:/proc/acpi/thermal_zone$ ls -a
.  ..
middle@The-Beast:/proc/acpi/thermal_zone$ 

I wish that there was just a list of what all of the sensors that are detected by lm-sensors was. Then i could just look it up. 

Or we can go through a process of elimination:

GPU tempreature {x} I can measure with 'aticonfig'
HDD tempreature {?} I doubt is is that as the tempreature increases with the cpu stress test
Sound card tempreature {x} My sound card is not plugged into anything, and again the tempreature rises during the cpu stress test
RAM {?} No idea
Wireless card {x} Cost £15 i doubt it
CPU {Maybe} *Fingers X'd*
Other Motherboard {?} No idea....

Is there any way that i can work this out via the process of elimination by like running tests on different hardware?

Cheers

EDIT: Just ran stress -d 50 -t 30 to test the HDD and there was no increase in tempreature

---

### Post by daqron on 2010-12-30
> **~Middle said:**
> Doesn't look like it =[ ...

I wish that there was just a list of what all of the sensors that are detected by lm-sensors was. Then i could just look it up. 
What about the stuff that was reported by sensors-detect? 

One more crazy idea ... do you have avant-window-navigator (AWN) installed? It has a hardware sensors applet that uses various tools to get its information. You could try that. [This post]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum&action=g_reply&ID=1779&page=1") explains what commands the applet uses. Not sure if it'll tell you anything new.

---

### Post by ~Middle on 2010-12-30
This is what 'sensors-detect' some out with:

Now follows a summary of the probes I have just done.
Just press ENTER to continue:  

Driver `k10temp' (autoloaded):
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK



The k10temp part looks like it is the processor but the pci-apadter label kind of nulls that....

There is a 2 character LED debugging panel on my motherboard and when it has booted up it looks like it is displaying a tempreature, I would assume it is the CPU tempreature as it looks realistic, also in my BIOS i can view the CPU temp, but unfortunately the debugging panel is showing a code at that time so i can't double check it. 

I could try awn but i kinda hate docks XD I will give it a shot to see though

Thanks a lot

---

### Post by drdos2006 on 2010-12-30
Right click the top toolbar, click on "Add to Panel", find "Hardware Sensors Monitor". This will show you the CPU temperature and motherboard temperatures.

regards

---

### Post by daqron on 2010-12-30
That temp might actually be your CPU. Possibly [see here]("http://lists.lm-sensors.org/pipermail/lm-sensors/2010-May/028526.html") for an explanation.
> 
[I]Jean Delvare wrote:
> On Sun, 09 May 2010 22:19:11 +0200, Florian Schwade wrote:
> > [florian at errorkiste ~]$ sensors
> > k10temp-pci-00c3
> > Adapter: PCI adapter
> > temp1:       +21.0°C  (high = +70.0°C)
> > 
> > 21°C is impossible to be the correct temperature. The BIOS reports my
> > CPU running at something like 36°.

The temperature values returned by k10temp are relative; AMD says:
| Tctl is the processor temperature control value, used by the platform to
| control cooling systems. Tctl is a non-physical temperature on an
| arbitrary scale measured in degrees. It does _not_ represent an actual
| physical temperature like die or case temperature. Instead, it specifies
| the processor temperature relative to the point at which the system must
| supply the maximum cooling for the processor's specified maximum case
| temperature and maximum thermal power dissipation.

Apparently, on your CPU, the reported values are about 15 °C lower.

lm-sensors currently does not indicate that values are not absolute.

> Maybe the BIOS applies an arbitrary offset,

AMD doesn't publish any method to derive this offset.

> or they get the temperature from an external sensor connected to a
> hardware monitoring device.

This is usually the case, especially since most mainboards also have
a bunch of other temperature sensors handled by the same hwmon device.
[/I]

---

### Post by ~Middle on 2010-12-30
So how would i interpret it? Just worry if it get above a certain level? or let smart-target fans do the work?



> **drdos2006 said:**
> Right click the top toolbar, click on "Add to Panel", find "Hardware Sensors Monitor". This will show you the CPU temperature and motherboard temperatures.

regards

This is showing the same tempreature as 'sensors'

Does that mean the k10temp-pci-blah is my CPU?

---

### Post by daqron on 2010-12-30
> **~Middle said:**
> Does that mean the k10temp-pci-blah is my CPU?
Yeah I think so. See above. My guess is that when the dude says "they get the temperature from an external sensor connected to a hardware monitoring device," that might explain why it's a PCI device reporting the (reliably incorrect) temperature.

---

### Post by ~Middle on 2010-12-30
OK so that means that my CPU tempreature is that of that sensor, however it has been adjusted for AMD's cooling... ok i will just have to use, that and say that my system tempreature is really low due to my amazing cooling XD

Thanks a lot for your help, this was really bugging me!

---

### Post by daqron on 2010-12-30
> **~Middle said:**
> ok i will just have to use, that and say that my system tempreature is really low due to my amazing cooling XD A sure way to impress many sexy ladies and/or dudes.

> **~Middle said:**
> Thanks a lot for your help, this was really bugging me!No problem. Air traffic control is a boring job so any distractions are always welcome.

---

### Post by ~Middle on 2010-12-30
hahaha lol i would hope you are paying some attention XD

If you ever need any help then contact me here: [http://bit.ly/dKDMdo](http://bit.ly/dKDMdo)

I can help you with that sort of stuff =]

---

