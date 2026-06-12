---
title: "ndiswrapper Help"
date: 2006-03-11
forum: General Help
---

### Post by Intell on 2006-03-11
I am using a WUSB54G(version 2) with the ndiswrapper.  
I installed the driver, modprobed, etc.  
I configured the settings (gateway, IP, DNS), but when I try to enable wlan0, it disables it 1 second later.  Any particular reason why?
KWifiManager says it's connected to my network with no local IP.

---

### Post by newbdude on 2006-03-11
Are you using WEP? If so, Kcontrol doesn't remember your key, but instead remembers the *********'s, and says that its an ASCII key. You have to edit a file somewhere in /etc/network, and enter your key, and change it to Hexadecimal key. As a rule of thum, NEVER use Kcontrol (thats the Networking tab under System Settings), theres a lot of bugs there.

---

### Post by carlos1 on 2006-03-11
If WEP is not the problem, I had this exact same problem. 
There are two things that I remember solving it: 
1) Making sure you have PCMCIA-utils (the package name may be worded slightly different but that is basically it) and 
2) Rebooting, with the device turned on and attached (I know it sounds like a Windows solution but the combination of the two things worked for me). 
I hope that helps.

---

