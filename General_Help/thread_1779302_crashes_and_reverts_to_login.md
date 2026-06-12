---
title: "crashes and reverts to login"
date: 2011-06-10
forum: General Help
---

### Post by Humphreybas on 2011-06-10
On my laptop (asus u31s, 64 bit intel i3) once in a while ubuntu crashes: screen suddenly goes black with some output for 0.1 sec and then takes me back to the login screen. It does not really happen systematically, this time I plugged in a SD-card (no problem) and then opened a image, upon opening it crashed.. But sometimes it crashes while I am working with firefox..

I checked the syslog but I am not sure what I am seeing is what caused the crash or what happened because of the crash:

(syslog after the last working thing I did before crash)
```
Jun 10 13:54:30 AapOFoon NetworkManager[835]: <info> (wlan0): device state change: 8 -> 3 (reason 38)
Jun 10 13:54:30 AapOFoon NetworkManager[835]: <info> (wlan0): deactivating device (reason: 38).
Jun 10 13:54:30 AapOFoon acpid: client 1044[0:0] has disconnected
Jun 10 13:54:30 AapOFoon acpid: client connected from 2212[0:0]
Jun 10 13:54:30 AapOFoon acpid: 1 client rule loaded
Jun 10 13:54:31 AapOFoon NetworkManager[835]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1725
Jun 10 13:54:31 AapOFoon kernel: [  621.199098] wlan0: deauthenticating from 00:23:cd:1f:50:c8 by local choice (reason=3)
Jun 10 13:54:31 AapOFoon wpa_supplicant[1050]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
Jun 10 13:54:31 AapOFoon kernel: [  621.368435] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun 10 13:54:31 AapOFoon kernel: [  621.368444] cfg80211: Restoring regulatory settings
Jun 10 13:54:31 AapOFoon kernel: [  621.368453] cfg80211: Calling CRDA to update world regulatory domain
Jun 10 13:54:31 AapOFoon kernel: [  621.375611] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Jun 10 13:54:31 AapOFoon kernel: [  621.375625] cfg80211: World regulatory domain updated:
etc.......
```

Does anyone know?
And any tips on how to solve this problem? (other log files I should check?)

---

