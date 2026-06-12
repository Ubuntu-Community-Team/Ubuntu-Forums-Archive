---
title: "NM Applet killed by resolution resize"
date: 2009-12-22
forum: General Help
---

### Post by TomRod on 2009-12-22
Howdy! Anytime my resolution is resized (via a game in WINE, or manually, or with any other kind of program requiring this [outside of flash--not sure if that actually resizes tho]) my nm applet disappears. While not a particularly heinous problem, this issue is annoying as it also disconnects me from the internet. While there may be other ways, I can only reconnect after killing X.

The following is the output from my syslog:

> Dec 22 09:37:20 dellicious NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 38 )
Dec 22 09:37:20 dellicious NetworkManager: <info>  (wlan0): deactivating device (reason: 38 ).
Dec 22 09:37:20 dellicious NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 5508
Dec 22 09:37:20 dellicious NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Dec 22 09:37:20 dellicious avahi-daemon[916]: Withdrawing address record for 192.168.1.3 on wlan0.
Dec 22 09:37:20 dellicious avahi-daemon[916]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.3.
Dec 22 09:37:20 dellicious kernel: [ 5312.514291] wlan0: disassociating by local choice (reason=3)
Dec 22 09:37:20 dellicious wpa_supplicant[1009]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Dec 22 09:37:20 dellicious avahi-daemon[916]: Interface wlan0.IPv4 no longer relevant for mDNS.
Dec 22 09:38:31 dellicious wpa_supplicant[1009]: CTRL-EVENT-SCAN-RESULTS 

(note: my computer is named dellicious)

lshw output at: [http://paste.ubuntu.com/344804/]("http://paste.ubuntu.com/344804/")

---

