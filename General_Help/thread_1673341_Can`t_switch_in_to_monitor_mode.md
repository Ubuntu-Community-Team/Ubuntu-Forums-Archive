---
title: "Can`t switch in to monitor mode"
date: 2011-01-22
forum: General Help
---

### Post by fredo994 on 2011-01-22
When i try to switch to monitor mode using airmon-ng start wlan0
i get an error 
"ERROR: modinfo: could not find module nvidia
wlan0			ath9k - [phy0]/usr/local/sbin/airmon-ng: 856: cannot create /sys/class/ieee80211/phy0/add_iface: Directory nonexistent
Error for wireless request "Set Mode" (8B06) :
    SET failed on device mon0 ; No such device.
mon0: ERROR while getting interface flags: No such device

				(monitor mode enabled on mon0)"
I  even found the script add_iface that should fix the problem but I was unabel to copy it in the /sys/class/ieee80211/phy0/ does anyone know how to fix this problem.

---

