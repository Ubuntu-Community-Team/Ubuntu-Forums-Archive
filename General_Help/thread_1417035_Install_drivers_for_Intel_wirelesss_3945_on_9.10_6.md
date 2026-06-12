---
title: "Install drivers for Intel wirelesss 3945 on 9.10 64bit"
date: 2010-02-26
forum: General Help
---

### Post by dardack on 2010-02-26
I had to send my laptop back for repairs, so I have an older Dell 1720 laptop that I threw the Hard Drive into, similar specs, just the wireless card is different.

So what i need to do is somehow activate the driver for the Intel 3945 wireless card in this dell laptop.  Anyone have any ideas?

---

### Post by WrierJeffs on 2010-02-26
> **dardack said:**
> I had to send my laptop back for repairs, so I have an older Dell 1720 laptop that I threw the Hard Drive into, similar specs, just the wireless card is different.

So what i need to do is somehow activate the driver for the Intel 3945 wireless card in this dell laptop.  Anyone have any ideas?

That pc card is supported [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel#miniPCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel#miniPCI) if its yours or
You can try installing the ndiswrapper package, instructions here [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by dardack on 2010-02-27
Yea sorry it's built into the kernel now I found out.  The reason i was panicking, was that ifconfig gave only lo interface, and iwconfig gave eth1, lo, wlan1, but wlan1 was limited it seemed.

And iwlist wlan1 scanning reported wlan1 doesn't support scanning.

However, just changing in WICD the wireless interface from wlan0 to wlan1 fixed it.  So happy guy right now.  At least partially until my newer laptop gets back.

---

