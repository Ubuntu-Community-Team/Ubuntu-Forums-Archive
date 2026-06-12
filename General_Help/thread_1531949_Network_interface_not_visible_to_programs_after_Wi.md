---
title: "Network interface not visible to programs after WiFi upgrade(10.4)"
date: 2010-07-15
forum: General Help
---

### Post by takaratiki on 2010-07-15
On ubuntu 10.4, I upgraded my laptop from a fluky Broadcom 4322 wireless card to a yummy Intel 5300. The system recognized the card as far as lspci and lshw were concerned, but it was disabled. I used "sudo ifconfig wlan0 up" to get it active, removed wicd and installed nmanager, and I could access the internet via web browser and mail. Yay.

The issue is that other programs (kismet, wireshark, zenmap, anything that I use at my job) do not recognize the new wlan0 interface at all. I've uninstalled completely from synaptic then reinstalled things like wireshark, but under interfaces I get nothing, not even eth0. Nothing looks askew in syslog or the relevant lshw/lspci searches. Does anyone have an idea on this? The Intel 5300 is rolling along without a hiccup so I doubt the issue is there. Additionally, is there an instruction set to follow for upgrading wifi hardware under ubuntu? Thank you.

---

### Post by takaratiki on 2010-07-16
Sorted the issue out as it mostly involved configuration files and failure to use gksudo for one program.

---

