---
title: "Random hard hangs in Natty server with SNB i3 H61"
date: 2011-06-01
forum: General Help
---

### Post by levk on 2011-06-01
I'm having random lock up issues on a brand new system, I'm hoping for some pointers because dmesg doesn't show anything useful and frankly I don't know where else to look.

It's a Natty server system, when it locks up I cannot ping the machine or ssh to it, nothing appears to be listening at all once it locks up. Connecting a monitor to it I see a mangled version of the login prompt - with randomly colored horizontal lines throughout. The machine is on 24/7 and this happens once every couple of days.

Directly on this box I have some routing going on through iptables and all that entails (with dnsmasq), linux raid setup with mdadm, and some virtualbox machines.

Hardware wise it's an i3-2100 Sandy Bridge, MSI H61M-P23 (B3) board, 8GB Corsair XMS RAM, D-Link DWA-556 WiFi, 3x Samsung Spinpoint F4 2TB each and a 16GB Kingston S100 SSD. Swap is spread on the spinners at 4GB each and everything else is raid'ed past that with home, var, and tmp on the raid volumes.

My current plan is to not launch any vbox machines on it and see if it's OK without them, I'm not sure if this is going to help since this appears to be hardware. Other than that I'm not sure what else I can try turning off.

---

