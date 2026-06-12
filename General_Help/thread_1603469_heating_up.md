---
title: "heating up"
date: 2010-10-22
forum: General Help
---

### Post by ulissipus on 2010-10-22
Hi! I am a fairly new user of Ubuntu. 
I've installed 10.10 in a Toshiba Portege R600 and I notice that the CPU is heating up in a way it did not with Windows 7. The cooler does not seem to turn on automatically.
My quetions: (1) how to monitor the CPU temperature? and (2) how to make sure the cooler/fan is working properly?
Though the CPU gets pretty warm, I think the temperature is still within acceptable limits, as the laptop doesn't turn off automatically.
Must say it gets very warm even when I am simply navigating in the 'net or doing an upgrade.
I've tried installing lm-sensors, but get the following message:

.
.
Reading state information... Done
lm-sensors is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by matt_symes on 2010-10-23
Hi

Open a terminal and type sensors. This will give you cpu temperature. Also there are panel applets for a more user friendly display

sudo apt-get install sensors-applet

This howto explains in more detail

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

This is a good general howto.

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

Kind regards

---

