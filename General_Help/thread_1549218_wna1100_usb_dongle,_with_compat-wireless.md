---
title: "wna1100 usb dongle, with compat-wireless"
date: 2010-08-09
forum: General Help
---

### Post by lostwolf on 2010-08-09
so, after hours of google, and an unnecessary clean install(apt-get'd compat-wirless rather than building the tar ball, and it played havoc on my kernal...) i've finally got at least a small amount of progress.

using compat-wireless-2.6 from thier website, and the ar9271.fw dmesg finds my dongle, correctly sees it as an atheros usb wifi card, but fails to initialize it...

modprobe -rf ndiswrapper
modprobe ath9k_htc
dmesg | grep ath

gives me 

[   10.084054] usb 1-10.3: ath9k_htc: Firmware - ar9271.fw not found
[   10.084078] ath9k_hif_usb: probe of 1-10.3:1.0 failed with error -22
[   10.084115] usbcore: registered new interface driver ath9k_hif_usb


so, what do?

oh, and ar9271.fw is in /lib/firmware, as well as several other directories, i thought that maybe the compat-wirless dir might be where i need to put it, but i cant find the darn thing...

---

