---
title: "Wireless Card Not Activated"
date: 2006-02-17
forum: General Help
---

### Post by dwessell on 2006-02-17
Hi all.

I had been running Ubuntu and it installed fine, picking up the Wireless Card (Dlink DWL 650+) just fine..

Today I deleted the partitions and installed Kubuntu.. At the time of install it was not able to find the network.. 

After the install I went into the network, and saw the card, but it was deactivated.. I attempted to activate it, but to no avail. I rebooted, to see what would happen. After the reboot, the card did not show up in the Network window.. I'm sure that the card works, as I have Windows on this same machine, and am writing this message through it.. Any recommendations would be welcome..

As well, in the KDE menus, I did not see the Synaptic Packet Manager, is it not in Kubuntu?

Thanks
David

---

### Post by gingermark on 2006-02-17
Kubuntu uses Adept rather than Synaptic as its package manager. If you prefer Synaptic, you can install it via Adept, or alternatively in Konsole type 'sudo apt-get install synaptic'.

I know little about wireless cards, but it does seem odd that your card worked with Ubuntu, but not Kubuntu, as their base is the same.

A quick google search suggests that the XP driver for your card will work with ndiswrapper, which is available in the repositories.

---

### Post by FlakJacket on 2006-02-17
When you try to activate it what exactly does it do.  I had a problem too and I'm wondering if yours is similar because then I might be able to help you.

Flak

---

### Post by dwessell on 2006-02-17
FlakJacket,

When I first attempted to activate it, I showed enabled for a few seconds. Then went back to disconnected.

After the reboot, it was gone though.. Quite strange as it worked under Ubuntu so well...

Thanks
David

---

### Post by dwessell on 2006-02-17
Problem solved..

I added this to /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
wireless-mode managed
wireless-essid xxxxxxxxxx
wireless-key xxxxx

All seems to be well...

Thanks all.

---

