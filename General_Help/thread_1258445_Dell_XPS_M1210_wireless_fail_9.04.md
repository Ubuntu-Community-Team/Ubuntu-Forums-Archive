---
title: "Dell XPS M1210 wireless fail 9.04"
date: 2009-09-05
forum: General Help
---

### Post by munchi3s on 2009-09-05
I have a Dell xps m1210 and the wireless drivers dont work. I dont know whats up. On installation of 9.04 I can activate the drivers(I think) and I do. But my computer wont see my wireless NIC. I dont have a wlan0 in ifconfig and, its just getting really frustating. 

Any help would be much appericatied. 
Thanks

---

### Post by jnorthr on 2009-09-05
often, the absence of a wlan0 device is symptomatic of an unknown hardware device. We can look in the log files that are generated at system startup for clues as to whas was wrong.

There is a menu option called 'logs' i think it's off the main menu. I'm not on my ubuntu system so will go look to see which one we need.

---

### Post by jnorthr on 2009-09-05
try System > Admininstration > Log File Viewer

then click on the syslog tab. This is a log file of messages that ubuntu generates at startup. 

Scroll to the bottom. Find todays date and the latest time. Read backwards from there. You should be able to find a time at which your system restarts. Then reading forward from there will be various messages about what hardware etc. is found. We're looking for anything 'wireless' or similar. Perhaps something about wlan0 or eth0 or ath0 ?

This might provide a clue as to what drivers are missing, not found, did not start, etc.

---

### Post by munchi3s on 2009-09-05
Ok. This is what I found


Sep  4 10:14:52 Ryan-Laptop kernel: [   12.444137] b43-phy0: Broadcom 4321 WLAN found
Sep  4 10:14:52 Ryan-Laptop kernel: [   12.488120] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 1)
Sep  4 10:14:52 Ryan-Laptop kernel: [   12.488156] b43: probe of ssb0:0 failed with error -95
Sep  4 10:14:52 Ryan-Laptop kernel: [   12.488195] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]

Here is the earliest
Sep  4 18:39:41 Ryan-Laptop kernel: [   12.466412] b43-phy0: Broadcom 4321 WLAN found
Sep  4 18:39:41 Ryan-Laptop kernel: [   12.509032] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 5, Type 4, Revision 1)
Sep  4 18:39:41 Ryan-Laptop kernel: [   12.509055] b43: probe of ssb0:0 failed with error -95
Sep  4 18:39:41 Ryan-Laptop kernel: [   12.509074] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]...
...Sep  4 23:44:39 Ryan-Laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch

---

### Post by P4man on 2009-09-05
maybe this helps?
[http://forums.msiwind.net/default-msiwind/broadcom-4321-ubuntu-t5055.html](http://forums.msiwind.net/default-msiwind/broadcom-4321-ubuntu-t5055.html)

---

### Post by munchi3s on 2009-09-05
I figured it out. In System > Administration > Hardware Drivers I was loading broadcom b43 wireless driver. Changed it to the broadcom STA wireless driver and everything worked like a charm.

Thanks for everyones help

---

