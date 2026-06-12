---
title: "Compiz fusion effects aren't working"
date: 2011-09-08
forum: General Help
---

### Post by abtekk on 2011-09-08
Hello, I have an Acer Aspire One D255 netbook with Ubuntu 10.10 installed. However the Compiz Fusion special effects aren't working, compiz is installed and so is the settings manager, however I select the effect I want (wobbly windows for example), click close and... Nothing, no effects, no change.

I have tried the _dpkg-reconfigure compiz-core_ command but still no luck. I'm pretty sure I have had it working on this laptop before.

---

### Post by zero2xiii on 2011-09-08
Your graphics drivers are probly not installed.

Go to System > Administration > Hardware drivers.. And install the needed drivers.

This is 90% of the time the cause of effects not working.

Cherz

---

### Post by Synoc on 2011-09-08
if it is an intel integrated video chipset, Compiz may be unable to work  properly or at all. if you have ensured the drivers are installed and  working properly, I would check to make certain you able to use the  effects. 

System>Preferences>Appearance: Visual effects tab. if you try  Extra and it tells you no, that is the moist likely culprit. it was for  me with my old laptop.

---

