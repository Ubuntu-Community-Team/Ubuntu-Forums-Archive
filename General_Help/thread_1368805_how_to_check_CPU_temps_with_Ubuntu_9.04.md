---
title: "how to check CPU temps with Ubuntu 9.04"
date: 2009-12-31
forum: General Help
---

### Post by Gatorade on 2009-12-31
I used to be able to check the CPU temps by opening a terminal and 

typing in this code

cat /proc/acpi/thermal_zone/THRM/temperature

but it doesn't work anymore , now I'm getting an error message saying 
"no such file or directory"

can someone tell me if there's another way to check the CPU temps?

---

### Post by x33a on 2009-12-31
try lm_sensors.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by Gatorade on 2009-12-31
someone recommended a different way to check the CPU temps, which I'm using now .

install sensors-applet in synaptic, once done' right click panel and hit add to panel, search for hardware sensors monitor, select and hit add.

I was wondering if anyone knows a way to monitor the GPU temps.

---

