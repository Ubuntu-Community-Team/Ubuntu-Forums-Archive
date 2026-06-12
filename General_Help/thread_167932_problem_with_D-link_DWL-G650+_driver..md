---
title: "problem with D-link DWL-G650+ driver."
date: 2006-04-29
forum: General Help
---

### Post by Flowing_air on 2006-04-29
I have installed ndiswrapper  and wirless tool.28. And i try to use:
ndiswrapper -i GPLUS.inf
to install driver.
and 
brant@CMGY:~/Download$ ndiswrapper -l
Installed ndis drivers:
gplus   driver present, hardware present

but when i enter "modprobe ndiswrapper",  it doesn't show me any thing, and light on wireless card is not on. It look like that i installed drive correctly, but the driver doesn't run.

Anyone know what is problem is?

This iwconfig command show some information maybe helpful..
brant@CMGY:~/Download$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  Nickname:"acx100 v0.2.0pre8"
iwconfig: symbol lookup error: iwconfig: undefined symbol: iw_sawap_ntop

---

### Post by vjkeito on 2008-05-27
bump.

---

