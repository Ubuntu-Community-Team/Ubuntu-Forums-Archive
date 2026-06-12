---
title: "lm_sensors"
date: 2010-05-27
forum: General Help
---

### Post by Drastic2010 on 2010-05-27
Hey guys,

So I would like to install lm_sensors to monitor my computer's health.  I try to run this code:

```
 sudo apt-get install lm_sensors 
```

And here's the output:

```
 E:  Couldn't find package lm_sensors 
```.

All of the HOWTOs I have inspected, have the initial step of running the sudo apt command, however I can't even do that.

Thanks in advance!
Drastic

---

### Post by Dilutu on 2010-05-27
Try lm-sensors, not lm_sensors.

---

### Post by Drastic2010 on 2010-05-27
Ok, so I ran lm-sensors and here's the code that I received:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up yiff-server (2.14.5-5.1) ...
Starting Y Sound Server: invoke-rc.d: initscript yiff-server, action "start" failed.
dpkg: error processing yiff-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 yiff-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Dilutu on 2010-05-27
So it seems lm-sensors is already installed .Maybe try to run "sudo sensors-detect".

---

