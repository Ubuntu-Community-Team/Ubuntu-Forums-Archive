---
title: "Somewhat happened to cpufreq"
date: 2011-10-14
forum: General Help
---

### Post by SushiR on 2011-10-14
Did anyone notice that you can't change the cpufreq governor to "ondemand" anymore? This happened after the last update. Can any of you confirm this?

---

### Post by lisati on 2011-10-14
I'm running 11.04 and still have "ondemand"......

---

### Post by SushiR on 2011-10-14
Sorry, forgot to mention that I'm running Oneiric...

---

### Post by flipper T on 2011-10-14
i installed jupiter, and on demand is selectable through this. 
however, for some reason, it is labeled "high performance"

---

### Post by matt_symes on 2011-10-14
Hi

Do you have it as an availiable governor ?

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```You change change it from the command line by

```
sudo bash -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
```This is for cpu0 only. Edit as required.

Kind regards

---

