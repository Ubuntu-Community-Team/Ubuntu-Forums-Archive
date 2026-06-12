---
title: "kill em all"
date: 2010-09-13
forum: General Help
---

### Post by xoadmox on 2010-09-13
hi iam in need of a bit of help iam trying to kill all these but they dont seem to want to die lol. ive tryed killall but the network manager doesnt go away and i even uninstalled it.
ad



Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
700    NetworkManager
719    avahi-daemon
723    avahi-daemon
822    wpa_supplicant
1312    dhclient
Process with PID 1312 (dhclient) is running on interface wlan0
qtronix@qtronix:~$

---

### Post by WorMzy on 2010-09-13
Try ```
killall -9 <processname>
``` and if that doesn't work, try it again with sudo.

---

### Post by xoadmox on 2010-09-13
thanks but ive tryed that and the network manager disconnects then comes back on and the process is still there.
ad

---

### Post by WorMzy on 2010-09-13
Does restarting help?

---

### Post by realzippy on 2010-09-13
network-manager still listed and checked in "Startup Applications"?

---

### Post by 98cwitr on 2010-09-13
dont worry about them...they're fine.

---

