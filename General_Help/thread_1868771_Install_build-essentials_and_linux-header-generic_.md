---
title: "Install build-essentials and linux-header-generic on Ubuntu Server"
date: 2011-10-24
forum: General Help
---

### Post by AmateurDev on 2011-10-24
I have an old computer that I want to turn into a server. When I installed Ubuntu Server 11.10, my wireless card was recognized and was able to connect to my wireless network. After rebooting, I cannot connect anymore. I suspect that the rt2800pci driver is to blame, so I built and copied the Ralink driver from another computer into /lib/modules/3.0.0-12-generic/kernel/drivers/staging/rt2860/rt2860sta.ko. I added rt2860sta to /etc/modules and blacklisted rt2800pci, r2800usb, etc and rebooted. Now when I run:
```
$lspci -k
```,
it shows that the wireless card has loaded rt2800pci and rt2860sta, without a driver to use it. Running ```
iwconfig
``` shows no wireless connections. I want to try to build it on the server, but I don't know how to install the package without an internet connection (there is no ethernet connection on this computer). Any suggestions or other possible solutions?

---

