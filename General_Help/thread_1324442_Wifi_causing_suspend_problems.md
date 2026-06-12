---
title: "Wifi causing suspend problems"
date: 2009-11-12
forum: General Help
---

### Post by jbrown96 on 2009-11-12
Running 9.10. 

My wifi is causing a problem with suspend. If I turn off my wifi switch, suspend and resume work fine. If the switch is on, it will suspend but will not resume. I just get a black screen (backlight is on) and I can't do anything (can't switch to a virtual terminal). I can leave the switch on, run ```
sudo ifconfig eth0 down
```, and suspend works fine. What's great is that wlan0 is brought back up on resume, so wifi reconnects. 

How can I force that command to run or fix the underlying issue? /etc/default/acpi-support does not seem to be used anymore, so I don't know where to turn. 

Thanks!

---

### Post by jbrown96 on 2009-11-12
Fixed it. I added ```
sudo ifconfig wlan0 down
``` to the second line of /usr/sbin/pm-suspend

---

