---
title: "Netgear WPN311 freezes Ubuntu 10.04 desktop"
date: 2010-05-10
forum: General Help
---

### Post by mrdoob on 2010-05-10
Since I installed Ubuntu 10.04 my desktop keeps freezing at random times. I removed the card and it didn't freeze anymore, so I'm pretty sure it's the card/driver.

These are the last lines on the syslog:

> May 11 02:49:59 mrdoob-desktop kernel: [ 9201.016017] No probe response from AP 00:1e:2a:12:8a:ac after 500ms, disconnecting.
May 11 02:49:59 mrdoob-desktop wpa_supplicant[997]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
May 11 02:49:59 mrdoob-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
May 11 02:49:59 mrdoob-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 11 02:50:00 mrdoob-desktop wpa_supplicant[997]: Trying to associate with 00:1e:2a:12:8a:ac (SSID='XPLSV' freq=2437 MHz)
May 11 02:50:00 mrdoob-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May 11 02:50:00 mrdoob-desktop kernel: [ 9202.278471] wlan0: direct probe to AP 00:1e:2a:12:8a:ac (try 1)
May 11 02:50:00 mrdoob-desktop kernel: [ 9202.281386] wlan0: direct probe responded
May 11 02:50:00 mrdoob-desktop kernel: [ 9202.281392] wlan0: authenticate with AP 00:1e:2a:12:8a:ac (try 1)
May 11 02:50:00 mrdoob-desktop kernel: [ 9202.283147] wlan0: authenticated
May 11 02:50:00 mrdoob-desktop kernel: [ 9202.283164] wlan0: associate with AP 00:1e:2a:12:8a:ac (try 1)
May 11 02:50:00 mrdoob-desktop wpa_supplicant[997]: Associated with 00:1e:2a:12:8a:ac
May 11 02:50:00 mrdoob-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
May 11 02:50:00 mrdoob-desktop kernel: [ 9202.285447] wlan0: RX AssocResp from 00:1e:2a:12:8a:ac (capab=0x411 status=0 aid=1)
May 11 02:50:00 mrdoob-desktop kernel: [ 9202.285450] wlan0: associated
May 11 02:50:01 mrdoob-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
May 11 02:50:01 mrdoob-desktop wpa_supplicant[997]: WPA: Key negotiation completed with 00:1e:2a:12:8a:ac [PTK=CCMP GTK=TKIP]
May 11 02:50:01 mrdoob-desktop wpa_supplicant[997]: CTRL-EVENT-CONNECTED - Connection to 00:1e:2a:12:8a:ac completed (reauth) [id=0 id_str=]
May 11 02:50:01 mrdoob-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
May 11 02:50:01 mrdoob-desktop NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed

It's using the ath5k driver.

Does anyone have any hint of what could I do?

---

### Post by Ge0Ks on 2010-05-16
Yes, its true...
I have the same wireless card (Netgear wpn311) and the same problem...

Any fix?

Regards

---

### Post by rdaussa on 2010-05-19
Same issue with NETGEAR WG111v3 USB.

It connects for a while (sometimes it freezes the router, always prevents other PCs to connect) and finally freezes ubuntu.

Noob to ubuntu, sorry if posted in the wrong forum, have no idea how to dump code on what happened.

R.

OS ubuntu 10.04

---

### Post by numberfiveandsix on 2010-07-05
The solution in this bug report [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356768/comments/30](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/356768/comments/30) (apparently) worked for me.

Computer has been continuously on for more than a day with heavy network traffic and without freezing :)

Oh and using Lucid (10.4)

---

