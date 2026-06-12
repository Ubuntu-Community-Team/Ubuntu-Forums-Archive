---
title: "problem with aircrack-ng"
date: 2011-12-13
forum: General Help
---

### Post by alibaba12 on 2011-12-13
hi,
i used for week or two usb live backtrack and everything work well.
now ive installed ubuntu with wubi,to be more fmiliar with linux.
my wireless card is : dell 1397 .
when i used backtrack my iterface name was wlan0 and now is eth1 with chipset " unknown" while at backtrack it was "Broadcom" if i remember right.

after i write airmon-ng start eth1,and try to scan with airodump-ng eth1 i get:
"ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.
"

tyvm for your help:)

---

### Post by Dangertux on 2011-12-13
Wubi is a virtualized install -- you can't access internal wifi through a virtualized install. You will need a USB wifi adapter or you will need to install it for real. (Or go back to BT)

Hope this helps :-/

---

### Post by CharlesA on 2011-12-13
> **Dangertux said:**
> Wubi is a virtualized install -- you can't access internal wifi through a virtualized install. You will need a USB wifi adapter or you will need to install it for real. (Or go back to BT)

Hope this helps :-/
What DT said.

Also, aircrack really isn't supported here.

---

