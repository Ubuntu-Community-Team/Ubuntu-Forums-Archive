---
title: "Sensors applet has 3 temperature gauges..."
date: 2009-09-17
forum: General Help
---

### Post by x C0MMAND0 x on 2009-09-17
I have always noticed this, but I have never asked.  There are 3 temperature sensors for the sensors applet I have installed.  GPU (graphics card) CPU (processor) and "libsensors".  What is "libsensors"?

See attached screenshot for more details.

---

### Post by undecim on 2009-09-17
> **x C0MMAND0 x said:**
> I have always noticed this, but I have never asked.  There are 3 temperature sensors for the sensors applet I have installed.  GPU (graphics card) CPU (processor) and "libsensors".  What is "libsensors"?

See attached screenshot for more details.

libsensors is a temperature that the app gets from the libsensors library. On my laptop, its the same as my CPU temperature. (Just accessed a different way I suppose)

unless you have another sensor in your computer somewhere, its probably just a copy of your CPU or GPU temp

---

### Post by skatinjj on 2009-09-17
That is interesting.  All I really know is libsensors is a package to read temperature,voltage, and fans.

Tried a quick google search but nothing helpful came up from what I saw.

---

### Post by x C0MMAND0 x on 2009-09-18
I have never been able to have it display any fan or voltage information either...perhaps I'm doing something wrong?  The "xsensors" program never works, only the "sensors-applet".  The "mystery" temperature gauge is almost always 1 or 2 degrees different than my CPU.  Perhaps it is reading the same part just in a different way?

---

### Post by fragos on 2009-09-18
To monitor sensors in general the Gnome environment you need to install lm-sensors, sensor-applet and libsensors. After installing lm-sensors run "sudo sensors-detect" which will configure your system for the sensors detected. The others will allow sensor display on the applet bar.

---

