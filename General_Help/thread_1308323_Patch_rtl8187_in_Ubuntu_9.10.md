---
title: "Patch rtl8187 in Ubuntu 9.10"
date: 2009-10-31
forum: General Help
---

### Post by simartem on 2009-10-31
My rtl8187 wireless device is shown like this in **airmon-ng** :

```

Interface    Chipset        Driver

wlan0        RTL8187     rtl8187 - [phy0]

nitro@abcd:~/Belgeler/wireless$ 

```

I am using Ubuntu Karmic Koala. How can i patch this rtl8187 driver for injection speed improvement ? I dont know if its better to use r8187 but as i've experienced before, it has problems with logging into WPA encrypted networks.. I found the patch for rtl8187 but i dont know where to save this patch and how to make it work, and which version ? The link to the patch is the following :

2.6.28 : [http://patches.aircrack-ng.org/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch](http://patches.aircrack-ng.org/rtl8187-mac80211-injection-speed-2.6.28-rc6.patch)
2.6.29 and up : [http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch](http://patches.aircrack-ng.org/mac80211-2.6.29-fix-tx-ctl-no-ack-retry-count.patch)

Any helps are greatly appreciated and NEEDED :)

---

### Post by simartem on 2009-10-31
any suggestions ?

---

### Post by Alacrity on 2009-11-14
Go here:

[http://forum.aircrack-ng.org/index.php?topic=5755.new#new](http://forum.aircrack-ng.org/index.php?topic=5755.new#new)

and you can see the choices.

A

---

