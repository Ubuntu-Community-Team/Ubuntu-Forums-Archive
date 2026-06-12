---
title: "Computer heating up"
date: 2011-09-21
forum: General Help
---

### Post by alxpenguin on 2011-09-21
Hi guys,

I feel like my laptop gets alot hotter when using Ubuntu than it does when I use Windows 7. Has this happened to anyone else? Is there anything I can do about it?

---

### Post by seawolf167 on 2011-09-21
The heat will depend on a lot of factors such as duration on, cpu usage, etc. Some things you can do to help it are to blow the dust out of all the fans/heatsinks, replace the thermal paste on the cpu (if it is really old), don't put it on things like carpet, try to elevate it for better air circulation, etc.

If I play a lot of Civ5 on my laptop it gets ***really* **hot :P

---

### Post by patryk77 on 2011-09-21
It's not really a solution, but you can monitor the temperature using the "sensors" program.

```
sudo apt-get install lm-sensors
sensors
```

```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +79.0°C  (crit = +127.0°C)                  
temp2:       +79.0°C  (crit = +110.0°C
```

(Yes, it's high, I am running two instances of fcrackzip)

If your temperature readings are indeed quite high, then we can look for the problem.

---

