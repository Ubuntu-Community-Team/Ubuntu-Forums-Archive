---
title: "Ubuntu 12.04 64-bit: VPNC Connection Stops All Network Connectivity"
date: 2012-05-02
forum: General Help
---

### Post by gristleizer on 2012-05-02
I've run into an odd problem using my newly rebuilt with Ubuntu 12.04 x-64 HP EliteBook 8540W: whenever I connect to corporate VPN (Cisco VPN where I have imported both the .pcf file from the Windows Cisco VPN client we use at work and tried building the VPN profile from scratch), I will get authenticated, be able to connect to corporate intranet sites for about 10 seconds, then my network connectivity just completely stops. The only way I can get network connectivity restored too is to reboot. Has anyone experienced this and, if so, do you know of a fix/workaround, because I'm trying to experiment with going Ubuntu as my main OS on my work laptop and would hate to quit the experiment and revert back to Windows. Thanks in advance for any suggestions/advice.

---

### Post by gristleizer on 2012-07-07
Sorry to bump this, but I've yet to run across anything to fix this. I actually was wrong in my original post: the way to restore network connectivity is to disconnect the Cisco VPN. Once that is done, I'm back to being able to hit all of the internet sites. But, VPN is still odd because it connects and I can connect to things for about 10-20 seconds tops, but then I have connectivity to nothing. I can't even ping the local router. Any tips would be greatly appreciated.

---

### Post by dino99 on 2012-07-07
its a known issue, and the workaround is done in #4 comment of this report:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1011991](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1011991)

---

### Post by gristleizer on 2012-07-07
I download and installed the .deb file from the link and I'm running into the same problem. Is there some special way in which I'm supposed to downgrade the app?

---

### Post by gristleizer on 2012-07-11
BUMP: Another thing...unlike other posts on this subject where people report that VPNC will work via terminal for them, the same thing happens to me whether or not VPNC is run terminal or GUI: VPN will connect but within a minute, all connectivity will be lost until I disconnect VPN. Any ideas anyone may have would be greatly appreciated.

---

### Post by gristleizer on 2012-07-19
**BUMP AGAIN**

So, tried to do the downgrade of the app. Still failing. I've also tried Shrew Soft VPN Access Manager and THAT is also running into the same problems. What can be going wrong? At this point, I'm trying to plot when would be a good time for me to move off all of my data and go with a fresh install of some other distro.

---

