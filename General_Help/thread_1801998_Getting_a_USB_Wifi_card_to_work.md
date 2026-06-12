---
title: "Getting a USB Wifi card to work"
date: 2011-07-11
forum: General Help
---

### Post by linuxuser12345 on 2011-07-11
Hi, I have a USB wifi card that works under 11.04, but not under any other version of Ubuntu. Is there a way I can gain support for this card in, say, a system running 10.04.2 or 10.10?? This is what the terminal tells me about the device:
```
jeb@Kitchen-PC:~$ dmesg | tail
[94303.916696] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[94303.916702] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[94303.916708] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (N/A mBi, 2000 mBm)
[94303.916870] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[94303.922396] Registered led device: ath9k-phy1::radio
[94303.922454] Registered led device: ath9k-phy1::assoc
[94303.922499] Registered led device: ath9k-phy1::tx
[94303.922546] Registered led device: ath9k-phy1::rx
[94303.922555] usb 2-4: ath9k_htc: USB layer initialized
[94304.156493] ADDRCONF(NETDEV_UP): wlan0: link is not ready
jeb@Kitchen-PC:~$ 

```

---

