---
title: "Karmic freezes up when setting an AP from a USB dongle with isl3887"
date: 2009-11-27
forum: General Help
---

### Post by bigshotpp on 2009-11-27
Hello, i'm trying to setup a Wireles Access Point with my Z-com Sitecom WL-125 WiFi USB dongle, which dmesg tells me has a isl3887 (p54) chipset. I have carefully followed the guides that describe how to set this up by bridging network interfaces and properly configuring hostapd. The thing is, i launch hostapd, everything works as intended, my iPhone sees the connection and connects to it (both in b and g mode, and with WPA2 and no security, i've tried all of those variants), but after that if i try to browse to new webpage, be it on my desktop or Mobile Safari, my computer completely locks up, it freezes and the Caps Lock and Scroll Lock leds blink. I've tried disabling avahi-daemon (i saw it on a log after the first reboot and disabled it just in case) but nothing changed. Any suggestions?

---

