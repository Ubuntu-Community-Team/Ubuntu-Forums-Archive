---
title: "lm_sensors at boot time"
date: 2011-06-12
forum: General Help
---

### Post by l3ecl on 2011-06-12
I managed to get lm-sensors working it has no initialization at bootime:

> Do you want to generate /etc/sysconfig/lm_sensors? (yes/NO): y
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.


I've already copied 'prog/init/lm_sensors.init' to '/etc/init.d/lm_sensors' but it doesn't work. I still have i manutally have to load 'coretemp' to be able to have a temperature output from the command "sensors"

---

### Post by gandaran on 2011-06-12
> **l3ecl said:**
> I managed to get lm-sensors working it has no initialization at bootime:



I've already copied 'prog/init/lm_sensors.init' to '/etc/init.d/lm_sensors' but it doesn't work. I still have i manutally have to load 'coretemp' to be able to have a temperature output from the command "sensors"
well, I don't really know what your problem is, when I ran sensors-detect I just type 'y' and enter to all questions, the program automatically adds the modules to the configuration files, no need to manually add anything then a reboot is all it needs to start working.

---

### Post by l3ecl on 2011-06-12
I also ran sensors-detect and I pressed 'y' to all the questions but it still doesn't load all the modules automatically.

I'm using lm-sensors 3.X

Since that happens, I always have to type 'modprobe coretemp' to manually load the modules.

---

### Post by wildmanne39 on 2011-06-12
> **l3ecl said:**
> I managed to get lm-sensors working it has no initialization at bootime:



I've already copied 'prog/init/lm_sensors.init' to '/etc/init.d/lm_sensors' but it doesn't work. I still have i manutally have to load 'coretemp' to be able to have a temperature output from the command "sensors"
Hi, I am not sure why it did not work, have you tried to go into startup applications and add it that way.

---

### Post by Yellow Pasque on 2011-06-12
> **wildmanne39 said:**
> Hi, I am not sure why it did not work, have you tried to go into startup applications and add it that way.
This is what the /etc/modules file is for..
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

So..
```
echo "coretemp" | sudo tee -a /etc/modules
```

---

### Post by l3ecl on 2011-06-12
hey it works! thanks a lot temujin (Genghis Khan) =P

---

