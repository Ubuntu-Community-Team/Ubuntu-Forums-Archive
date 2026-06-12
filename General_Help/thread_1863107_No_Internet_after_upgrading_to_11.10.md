---
title: "No Internet after upgrading to 11.10"
date: 2011-10-17
forum: General Help
---

### Post by guyfromfl on 2011-10-17
I upgraded on Thursday, and have had a ton of problems. 

One is the internet now does not work.  

I had to install a D-Link DFE-530TX+ because the onboard Realtek RTL8111DL was not compatible in 11.04, assuming the same for 11.10.

Last week, The internet was working fine after the upgrade.  This morning when I got to work, no internet.

I can access the LAN, but not get on the internet.

I am running a static IP and everything in /etc/network/interfaces is correct.

The only thing I am worried about is if I run ifconfig, eth0 (the Realtek) and eth1 (D-Link NIC I want) are listed.  Could this be causing conflict?  There is no entry for eth0 in interfaces.

Please help me my work is piling up and I really don't want to give up and remain in windows.  My old setup worked so well.

---

### Post by guyfromfl on 2011-10-17
I am on the same machine right now, dual-booted into Windows 7 for the internet to get help... 

This means there is no hardware issues.

---

### Post by phil0stine on 2011-10-18
Same here. I have a Dell xps studio, broadcom wifi chipset.

---

