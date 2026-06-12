---
title: "Wireless connection problems"
date: 2009-12-02
forum: General Help
---

### Post by Mixalis0 on 2009-12-02
Hello all,

I'm running Jaunty on a Lenovo T61 notebook, and I have a very peculiar (or so I think) and frustrating problem. I can connect to every wireless network that I've encountered except for the one I have set up at home. At first, after having read much about problems with the iwlagn driver when attempting to connect to networks with WPA2 security, I installed various upgrades for network-manager. None worked. 

In attempt to connect using my own network instead of leeching off of the linksys family next-door, I dumbed-down my network's security to WPA, then WEP, then nothing, and I still can detect no signal.

However, when using a different computer that runs Windows, I have no problems connecting to the network, whether it has WPA2, WPA, WEP, or no security at all. Even using the same computer (of course with the same Intel PRO/Wireless 4965 AGN network card), I can find the network at any time when I boot Vista instead of Ubuntu.

The worst part: when I'm running Ubuntu, I can detect nearby networks with *any* security protocol, including WPA2. This is so frustrating, and any help you could offer would be greatly appreciated. Thanks.

---

### Post by Some Penguin on 2009-12-02
Verify 

1) that your router is broadcasting the SSID
2) that your TKIP -vs- CCMP/AES setting is correct

---

### Post by Mixalis0 on 2009-12-02
My router is definitely broadcasting the SSID; it's shown in the "available wireless networks" lists of any Windows computers that I've tried (I have no other Linux machines to test). As for TKIP vs AES, the normal security settings that I have enabled are "WPA-PSK [TKIP] + WPA2-PSK [AES]." When I tried reducing the security, I moved down to "WPA2-PSK [AES]" and then "WPA-PSK [TKIP]." This is all I see in the way of TKIP vs AES settings on the machine attached to the router. As for my notebook, I have no idea where to look to adjust similar settings. Any thoughts?

---

