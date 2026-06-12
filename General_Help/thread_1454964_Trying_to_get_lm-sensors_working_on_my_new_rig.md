---
title: "Trying to get lm-sensors working on my new rig?"
date: 2010-04-15
forum: General Help
---

### Post by chisle on 2010-04-15
I been trying to get lm-sensors working. i just built my new computer and been trying to monitor the temps, so i can make sure it is stable. i have run "sensors-detect" and answer yes to every questions. the output i get is this:

"Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `Nuvoton W83677HG-I Super IO Sensors' (confidence: 9)

Driver `k10temp':
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Note: there is no driver for Nuvoton W83677HG-I Super IO Sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK"

So i go to [ http://www.lm-sensors.org/wiki/Devices]("http://www.lm-sensors.org/wiki/Devices") and even find the drivers it is looking for, but dont know what to do from there. what do i have to do from here to get lm-sensors working? thank you for the help in advanced.

---

### Post by bwhite82 on 2010-04-15
Alright,

It seems that you have very new hardware and things are currently under development. It looks like the k10temp module you can compile, the other is not yet written. It depends on how comfortable you are compiling and linux in general:

-If you are a new(ish) user, I recommend waiting a couple of months (best guess) for your hardware until these modules are compiled into Ubuntu's newest kernel.

-If you don't mind getting your hands dirty, you can compile the k10temp module by going to the terminal and:

> wget [http://khali.linux-fr.org/devel/misc/k10temp/Makefile](http://khali.linux-fr.org/devel/misc/k10temp/Makefile)
wget [http://khali.linux-fr.org/devel/misc/k10temp/k10temp.c](http://khali.linux-fr.org/devel/misc/k10temp/k10temp.c)
make
sudo make install

You will need to do this will each new kernel until it is added natively

---

### Post by chisle on 2010-04-15
so i found this thread: [http://newyork.ubuntuforums.org/showthread.php?t=1287819](http://newyork.ubuntuforums.org/showthread.php?t=1287819)
and follwed what it had to say after i downloaded the k10temp.c file that matched the driver it said i needed for the amd 10th family...
and way now my read out i get when i type "sensors" into the terminal is 0C. so it is detecting something but reads as 0 degrees. and apparently there is no driver right now for the other sensor it detects. any one help please. i like to overclock but it makes it very hard to do so if i can;t monitor my temps.

---

### Post by chisle on 2010-04-15
> **Soldierboy said:**
> Alright,

It seems that you have very new hardware and things are currently under development. It looks like the k10temp module you can compile, the other is not yet written. It depends on how comfortable you are compiling and linux in general:

-If you are a new(ish) user, I recommend waiting a couple of months (best guess) for your hardware until these modules are compiled into Ubuntu's newest kernel.

-If you don't mind getting your hands dirty, you can compile the k10temp module by going to the terminal and:



You will need to do this will each new kernel until it is added natively

i believe the thread i found was how to compile the k10temp.c like you were saying correct? so once it comes out natively will it automatically replace the file i just put there? and yes actually the motherboard i am using just came out in the U.S. last week. its an ASRock 890gx extreme3 motherboard

P.S. your directions were easier than that thread lol.

---

### Post by chisle on 2010-04-16
bump?

---

### Post by bwhite82 on 2010-04-16
> **chisle said:**
> i believe the thread i found was how to compile the k10temp.c like you were saying correct? so once it comes out natively will it automatically replace the file i just put there? and yes actually the motherboard i am using just came out in the U.S. last week. its an ASRock 890gx extreme3 motherboard

P.S. your directions were easier than that thread lol.

Yes, my instructions were for compiling. Did it do the trick? You'll have to wait until devs get your other sensors working. Keep checking the page you linked to. Once a new kernel upgrade is released. Check to see if your sensors are reporting. If not then recompile the module. Keep doing this until a kernel is released that includes your modules.

---

