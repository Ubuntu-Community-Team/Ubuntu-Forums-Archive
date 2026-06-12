---
title: "falling back on xorg?"
date: 2006-06-17
forum: General Help
---

### Post by LORD_PoLvO on 2006-06-17
hey all need some help, i upgraded my nvidia drivers to latest version but when i load up X it crashes.
i change nvidia to nv in xorg.conf and the system seems to load fine yet i do not get any nvidia logo and when i load up nvidia-settings in terminal/konsole i get the following.
```
daniel@CPE-60-227-116-7:~$ sudo nvidia-settings
Password:

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.




```


when i try glxgers in terminal/konsole i get a segmentation error

```
daniel@CPE-60-227-116-7:~$ glxgears
Segmentation fault
daniel@CPE-60-227-116-7:~$



```

can anyone tell me how i can fall back on a backed-up verion of my xorg config please?

---

### Post by tseliot on 2006-06-17
Please try my script (it should clean the mess on your computer):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

NOTE: MAKE sure you use the latest version

---

