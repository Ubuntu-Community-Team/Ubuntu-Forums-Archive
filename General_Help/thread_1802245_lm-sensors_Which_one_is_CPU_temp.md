---
title: "lm-sensors: Which one is CPU temp?"
date: 2011-07-11
forum: General Help
---

### Post by dzwestwindsor on 2011-07-11
I have an Athlon Dual Core

When I run "sensors", part of my output is this:

```

temp1:       +45.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +42.0°C  (low  = +127.0°C, high = +60.0°C)  sensor = thermal diode
temp3:       +46.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor

```Okay, 3 temperature readings. Which one do I look at? Which one is my CPU temp? Is there motherboard temp?

How do I distinguish between the temperatures?

---

### Post by pqwoerituytrueiwoq on 2011-07-11
try using the sensors applet
it names them something readable with the exception of one that appeared today
sudo apt-get install sensors-applet
then add it to the panel like any other applet
edit the sensors command has the same names
what hardware do you have my laptop has a temp for each core

---

### Post by colin.p on 2011-07-12
I'm not sure what temp 1 is, but I use core 0 and core 1 in my sensors applet. Temp 1 is always a degree or two from core 0,1, so I figure it must be an average of the two cores, which makes sense as it is only one physical chip, just two cores. It hasn't blown up on me yet.

---

### Post by dzwestwindsor on 2011-07-12
Colin,

Thanks, for some reason I don't get core temp readings... 

Temp2 seems to fluctuate a lot.. is that a sign that it's CPU temp? Temp 1 and Temp 3 seems to rise slowly and steadily. Does your CPU temp fluctuate as well? I get a different reading every 10 seconds or so for temp2 

Are there thermometers on each of my cores? Do you know what the most common places to find the thermometers are? (ie, 1 on CPU, 1 on motherboard, etc)

Thanks

---

### Post by psusi on 2011-07-12
Typically temp1 is the cpu, but it varies from motherboard to motherboard.  If you have a P4 cpu, then you want to load the pkgtemp and coretemp modules to get the cpu internal sensors.

---

### Post by colin.p on 2011-07-13
> **dzwestwindsor said:**
> Colin,

Temp2 seems to fluctuate a lot.. is that a sign that it's CPU temp? Temp 1 and Temp 3 seems to rise slowly and steadily. Does your CPU temp fluctuate as well? I get a different reading every 10 seconds or so for temp2 

Thanks

I have an Intel T-4400 dual core CPU (Dell laptop). I only have core 0 and core 1 monitoring, as I said, temp 1 seems to be a reading of both cores together, rather redundant. Yes, the temp is constantly fluctuating by a couple of degrees, and yes there is a different reading from each core.

---

