---
title: "ndiswrapper issues with dhcp"
date: 2006-01-26
forum: General Help
---

### Post by klepto on 2006-01-26
I've compiled ndiswrappers, installed it and used my devices inf and sys file
with no errors. The device comes up but it will not take an ip address.

Any ideas? 

It is a Broadcom bcm4306.
[4297833.918000] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[4297834.014000] ndiswrapper: driver bcmwl5 (Broadcom,04/21/2005, 3.100.65.1) loaded
[4297834.014000] ACPI: PCI Interrupt 0000:05:02.0[A] -> GSI 20 (level, low) -> IRQ 20
[4297834.026000] ndiswrapper: using irq 20
[4297834.534000] wlan0: ndiswrapper ethernet device 00:14:a5:14:1e:b8 using driver bcmwl5, configuration file 14E4:4320:103C:12F8.5.conf
[4297834.534000] wlan0: encryption modes supported: WEP, WPA with TKIP, WPA with AES/CCMP
[4297879.132000] wlan0: no IPv6 routers present

here is my lspci info
0000:05:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by klepto on 2006-02-05
Ok, fixed..

FOR INFORMATIONAL PURPOSES:

If you are like me and don't read all the readme(s) carefully.
wpa_supplicant does not build the ndiswrapper drivers by default
you have to enable them.

The latest version of ndiswrapper works well with broadcom drivers.
if you have any issues remove the acx folder in your default kernel folder.

---

