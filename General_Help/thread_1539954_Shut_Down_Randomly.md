---
title: "Shut Down Randomly"
date: 2010-07-27
forum: General Help
---

### Post by SasukeUchihaXlll on 2010-07-27
Yeah i was searching the web and doing some other stuff with my Ubuntu USB 10.04 on my laptop and after maybe 3 - 5 hours it'd shut down for no reason. Kernel Version : 2.6.32-24-generic

---

### Post by josephpmh on 2010-07-27
Can you give us a brief description of your hardware?  And do you use a hardware monitor like lmsensors (see [help.ubuntu.com/community/SensorInstallHowto]("http://help.ubuntu.com/community/SensorsInstallHowTo") for installing and adding to the panel).  If so, could you also report the temperature(s) of your CPU core(s).  While PC hardware is a bit more tolerant of heat than we humans, get ready for a auto shutdown when temps start to climb towards 70C.

---

### Post by Krabby.Linux on 2010-07-27
This can be a Temperature problem. 

> 
sudo apt-get install sensors-applet

Install it and than Rightclick on your Panel ... Add Panel ... Hardware Sensors Monitor and take a look on the Temperatures.

---

### Post by SasukeUchihaXlll on 2010-07-27
Alright i installed the sensors, and to the previous comment of the laptop its a Lenovo R61i, With a Intel Core 2 Duo T5250, 2 GB of Memory and 1.50 GHz.

---

