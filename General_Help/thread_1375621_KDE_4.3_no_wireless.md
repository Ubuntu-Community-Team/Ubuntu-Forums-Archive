---
title: "KDE 4.3 no wireless?"
date: 2010-01-08
forum: General Help
---

### Post by JECHO on 2010-01-08
Hey guys, Ive got Ubuntu 9.10 installed on my Macbook Pro 5,5 and everything is working... I decided to install the Kubuntu desktop package along side gnome and when i boot into KDE, wireless does not work. Its not picking up on any networks even though wireless is checked as active. Any ideas? I haven't been able to find anything through google.

---

### Post by Zorael on 2010-01-08
**edit**: Wait, it's working in GNOME but not in KDE?

The terminal command to scan for networks;
```
$ sudo iwlist scan
```
It should output a list of discovered ESSIDs. If it finds stuff and knetworkmanager doesn't report them, something is indeed wrong with the latter. You may have better luck using **wicd**, but changing to that means you'd have to use that in GNOME, too.

If it's not working in either environment, I see over on [the wiki page for MacBook Pro 5.5s](https://help.ubuntu.com/community/MacBookPro5-5/Karmic) that wireless needs to be installed manually. The instructions seem short and easy enough, though.

---

### Post by edd07 on 2010-01-08
I also recommend using wicd, it works better for me than knetwork-manager.

---

### Post by JECHO on 2010-01-08
thanks guys, wicd worked well. :) Yeah its strange, it works fine in gnome but not in KDE.

---

### Post by zehnmonkey on 2010-01-09
Not a total noob, but only been working linux about a year after getting outside my MCSE comfort zone.  That's a whole other post though. . .

Got the same issue on a brand new Dell XPS 1640, however my card is an intel pro wireless 5300 agn, which is supposedly included in the kernel.  Tried both WICD and the crappy netmon.  The card simply detects no networks.  

I tried the command to check available networks and it says the "interface doesn't support scanning: the network is down."

Intel does not have a driver file to download since it's included in the kernel.   

Little help?

---

### Post by sanjoe on 2010-03-14
In the settings>connections secrets, keep the password unencrypted.. this works !!

---

