---
title: "Cyberpower UPS support"
date: 2010-03-13
forum: General Help
---

### Post by daldude on 2010-03-13
I have a Cyberpower CPS700 AVR UPS system and I went to 
[http://www.cyberpowersystems.com/products/management-software/ppl.html?selectedTabId=downloads&imageI=#tab-box](http://www.cyberpowersystems.com/products/management-software/ppl.html?selectedTabId=downloads&imageI=#tab-box)
 
and downloaded and installed the
[PowerPanel for 64 bit Linux .deb 1.1.4 (Linux 64 bit)]("http://www.cyberpowersystems.com/software/powerpanel_1.1.4_amd64.deb")
software and it seemed to install ok because it said installation complete and did not report any errors but when I type the command pwrstat -status in a terminal window it gives me a message
Daemon service is not found
I opened the Synaptic Package Manger and found Daemon and marked it for installation and rebooted but I still get the Daemon service is not found error when I try to run the pwrstat program. If I type pwrstat -help it brings up a list of all the commands so that seems to mean the program is installed.

How do I get it to work properly so it can control my UPS if I have a extended power 
failure?

Umbuntu's Power Management can see my APC UPS but not the Cyberpower and I would like to use the Cyberpower because it is a 700VA and has AVR while the APC is only 500va and has no AVR.


               Thanks:P

---

### Post by Rocket2DMn on 2010-09-26
I know it's probably a little late for a response, but I ran across this thread while looking up info on this utility.  You need to use sudo with the pwrstat command, otherwise it will say it can't find the service.  Hope that helps somebody in the future :)

---

### Post by Mike'sHardLinux on 2010-10-07
Thanks Rocket2DMn! I just cheaped out and gambled on a CyberPower UPS and that probably saved me a few minutes of noodling around/googling.

---

