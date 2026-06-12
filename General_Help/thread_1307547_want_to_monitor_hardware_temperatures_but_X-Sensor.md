---
title: "want to monitor hardware temperatures but X-Sensors wont load"
date: 2009-10-31
forum: General Help
---

### Post by Vigh on 2009-10-31
Hi I want to monitor my hardware temperatures but when I install with add/remove X-Sensors, it refuses to load, is there any other programs out there for monitoring hardware temps in linux

---

### Post by SuperSonic4 on 2009-10-31
Can't you just run *sensors* in terminal?

You might also want to check for *lm-sensors* (should be a dependency of X-sensors though) and try running ```
sudo sensors-detect
``` if that doesn't work

---

### Post by Vigh on 2009-10-31
still not working, i ran sensors detect, and also checked that i had the lm-sensors module installed, running sensors through the terminal doesnt work either

---

### Post by cariboo on 2009-10-31
Did you load the modules manually, or restart the computer? None of the sensors will show an output until the modules are loaded.

To check if the modules are loaded check with the list in /etc/sensors.conf to see which modules were found.

---

### Post by Vigh on 2009-10-31
will try restarting after doing sensor-detect, 

no luck, sensors still not working

---

