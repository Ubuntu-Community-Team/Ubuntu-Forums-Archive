---
title: "Modprobe of ieee802_crypt_wep.ko FATAL"
date: 2006-03-13
forum: General Help
---

### Post by AV215 on 2006-03-13
To get wep support for my ipw2200 I need to add the ieee80211_crypt_wep module to my kernel.

I enter:
```
sudo modprobe /lib/modules/2.6.12_10_686/kernel/drivers/net/wireless/ieee80211/ieee80211_crype_wep.ko
```

And it return ```
FATAL /lib/modules/2.6.12_10_686/kernel/drivers/net/wireless/ieee80211/ieee80211_crype_wep.ko nnot found
```

Doing an ls reports that the module is there.  Why isn't it loading?

---

