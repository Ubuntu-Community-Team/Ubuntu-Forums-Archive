---
title: "network-manager won't die / System not shutting down properly"
date: 2012-02-09
forum: General Help
---

### Post by Claritux on 2012-02-09
I've been having issues with the system not shutting down properly, forcing me to do a REISUB every time I try to shutdown/reboot the computer. The problem seems to be that the system is unable to kill remaining processes and I've tracked this down to the network manager. I plan to do a purge remove of network-manager and network-manager-gnome and reinstall to see if that fixes the problem, but I am unable to do so because the network-manager process won't die whatever I do. (sudo service network-manager stop / killall network-manager / /etc/init.d/network-manager stop. Nothing works). Another weird thing is that after trying to kill network-manager I can't use any terminal commands (just gives a blinking cursor). Can anybody help me prevent network-manager start in the first place so I can remove it or come up with another solution?

Ubuntu 11.10 64-bit

---

### Post by Claritux on 2012-02-09
Just had another go at uninstalling network-manager and this time the whole system froze so badly I couldn't even REISUB myself out of it. *getting a bit frustrated about this*

---

### Post by Claritux on 2012-02-10
I've had quite the job trying to fix this now. Just to mention what I've been trying:
Tried to apply fixes according to theese bugreports, didn't work:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/869635)
[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825)

Tried to replace network-manager with wicd. (I were able to uninstall network-manager as long as I prevented it to connect to the wireless after boot. Ctrl+Alt+F2 before login and uninstall or turn off your wireless router). Made no difference exept that I were unable to use REISUB at halt.

In the end the problem seems to be my wireless card, a Ralink R2561. As a temporary solution I've blacklisted the wireless card (add "blacklist rt61pci" to /etc/modprobe.d/blacklist.conf) and am using USB-tethering with my phone as a replacement. Probably going to buy a network cable.

---

