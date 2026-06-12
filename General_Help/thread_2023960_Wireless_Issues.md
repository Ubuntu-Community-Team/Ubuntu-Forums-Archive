---
title: "Wireless Issues"
date: 2012-07-13
forum: General Help
---

### Post by Rsjc741 on 2012-07-13
I ramble (if you've read any of my other help threads), so I'll keep this short.
 
OS - 12.04
 
Model - Linksys WMP300N
 
Proven to work - Sorta. Firmware release by Broadcom is out, but is pretty poor.
 
Chipset - US. Brcm4321 chipset
 
Problem - Horrible download speeds ( <400KB/s. Should be 2-4MB/s). Webpages take forever to load. Connection will drop under 3/4 bar conditions. Causes frequent system halts(Could be graphics card). Won't connect now. Says SSID is wrong.
 
 
Help?

---

### Post by todak on 2012-07-13
You can either install ***ndisgtk*** from the repositories, or return the wi-fi adapter you have and get one based on the Atheros chipset. I use a Netgear WNA1100 and it is truly plug and play in Ubuntu.

---

### Post by Rsjc741 on 2012-07-13
I've tried using Ndiswrapper on other Ubuntu versions before the brcm43xx firmware was released. It was really hit or miss.
 
I doubt I could return it... I've had the thing for 3 years now.
 
I think im going to use my brother's Linksys AE2500. It's USB, so I imagine it's more PNP than a 3 year old PCI adapter.
 
 
Then I'll hijack my own thread.
 
 
I'm also having graphics issues!
 
- Nvidia PNY GTX 560 Ti XLR8 Series
 
- This thing was recognized and worked awesome during installation. Afterwards, xserver would crash until I had to manually wget and sh the nvidia installer. Xserver will still crash on start up (rather, the login screen) and revert back to Unity 2D (I guess.. i've never seen 3D?) Graphics adapter in Settings shows up as Unknown with 4096mb of memory. It likes to hang the system.. especially after going into sleep for a long period of time.
 
 
After it initially crashes, the login screen, which is NOT suppose to show up in the first place, turns black. Then it turns back on, this time with white dots spaced every 30px or so on the login screen.
 
Help?

---

