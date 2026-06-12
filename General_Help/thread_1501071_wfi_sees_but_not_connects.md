---
title: "wfi sees but not connects"
date: 2010-06-03
forum: General Help
---

### Post by colorlessprism on 2010-06-03
i downloaded and installed moblin remix. my computer sees the wireless network asks for my wep key and attempts to connect. i am told it fails:

rtl8187se

lines from dmesg:
 rtl8187se: module is from the staging directory, the quality is unknown, you have been warned.

~~
9.703668] r8180: Bringing up iface
[    9.904576] r8180: Card successfully reset
[   10.652049] r8180: WIRELESS_MODE_G
[   10.652054] 
[   10.671653] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.860110] Skipping EDID probe due to cached edid
[   18.919088] Skipping EDID probe due to cached edid
[   18.946122] Skipping EDID probe due to cached edid
[   26.500103] Clocksource tsc unstable (delta = -307804059 ns)
[   70.146417] Linking with Nexus: channel is 6
[   70.187332] Linking with Nexus: channel is 6
[   70.231278] Linking with Nexus: channel is 6
[   70.275050] r8180: Setting SW wep key
[   70.362038] r8180: Setting SW wep key
<this continues many lines>
   74.967643] In rtl8180_set_chan: Invalid chnanel 16
[   75.012042] r8180: Setting SW wep key
[   75.095048] r8180: Setting SW wep key
[   75.179037] r8180: Setting SW wep key
[   75.263039] r8180: Setting SW wep key
[   75.345053] r8180: Setting SW wep key
[   75.429039] r8180: Setting SW wep key
[   75.510788] r8180: Setting SW wep key
[   75.538332] In rtl8180_set_chan: Invalid chnanel 18
<and the cycle continues>

please let me know if you can help. my google fu is weak on this topic

---

### Post by gabak on 2010-06-03
1-remove wep from router and see if it works. if it does , change encryption mode.
wep o wpa , etc.

---

### Post by colorlessprism on 2010-06-04
removing encryption results in the same. i can see the network it will attempt to connect, say it is "associating" and then says it fails

---

