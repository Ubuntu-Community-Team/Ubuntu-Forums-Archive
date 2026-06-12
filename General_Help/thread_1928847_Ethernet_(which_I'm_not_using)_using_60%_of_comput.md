---
title: "Ethernet (which I'm not using) using 60% of computer's power?"
date: 2012-02-20
forum: General Help
---

### Post by steevven1 on 2012-02-20
I noticed something strange from PowerTOP today. My laptop only burns about 8-9 Watts of power, but PowerTOP claims that 5-6 Watts of that comes from my ethernet (which I am not using at all...it's not even plugged in). How can this be? Any suggestions? Screenshot attached. Thanks.

---

### Post by wildmanne39 on 2012-02-20
Hi, you can go into your bios and see if you can turn it off, if not post the output of:
```
lspci -nnk | grep -iA2 net
```
and we can blacklist the driver but then it will not work if you want it too without unblacklisting it.
Thanks

---

### Post by mikewhatever on 2012-02-20
Could be the Wake On LAN feature, though it's highly unlikely that it really draws 5W of power.
[http://lesswatts.org/tips/ethernet.php](http://lesswatts.org/tips/ethernet.php)

---

### Post by steevven1 on 2012-02-21
I cannot turn ethernet off altogether in the BIOS, but Wake-on-LAN was already off in the BIOS. As for the output of the lspci command:

```
[01:27:03 | steven]<~>$ lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlwifi

```Thank you for the help!

---

### Post by wildmanne39 on 2012-02-21
Hi, please do this and see if that helps.
```
echo "blacklist e1000e" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot.
Thanks

---

### Post by steevven1 on 2012-02-21
No change. Ethernet still listed as using 5 W in PowerTOP; overall power consumption still the same. Maybe it's just an error in PowerTOP? Any other ideas? Thanks!

---

### Post by wildmanne39 on 2012-02-21
Hi, > Maybe it's just an error in PowerTOP?I thought the same thing, I researched it but I did not find an answer.
Thanks

---

