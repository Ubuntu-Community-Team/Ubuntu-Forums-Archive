---
title: "bug in wpasupplicant"
date: 2010-12-25
forum: General Help
---

### Post by ruben_linux on 2010-12-25
hi people. i'm using ubuntu 10.04 lts 2.6.32-24-generic, wifi AR9285 Wireless Network Adapter (PCI-Express), driver=ath9k. my wpasupplicant version is 0.6.9-3ubuntu3

in this web: [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/578431](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/578431) report a bug, "wpa_supplicant spams syslog"
Yesterday i update my system and the problem began.

my syslog, reportme all the time:

CoYoTe wpa_supplicant[1049]: WPS-AP-AVAILABLE

and

CoYoTe wpa_supplicant[1103]: Trying to associate with 00:14:a5:05:e4:2b (SSID='Motorola' freq=2412 MHz)
CoYoTe wpa_supplicant[1103]: Association request to the driver failed
CoYoTe NetworkManager: (wlan0): supplicant connection state: scanning -> associating
CoYoTe wpa_supplicant[1103]: Authentication with 00:14:a5:05:e4:2b timed out.
CoYoTe NetworkManager: (wlan0): supplicant connection state: associating -> disconnected
CoYoTe NetworkManager: (wlan0): supplicant connection state: disconnected -> scanning

i need help.

---

