---
title: "wireless scanning"
date: 2006-04-03
forum: General Help
---

### Post by paradox814 on 2006-04-03
I am trying to get my card to scan for available wireless networks but I don't see a way to with the default setup.

so I downloaded and installed [GTKWifi]("http://gtkwifi.sourceforge.net/") (which looks like exactly what I want) but it says my card does not support scanning?!? It works just fine in windows, what can I do? I am a student and because of spotty wireless reception on campus most teachers have installed their own access points, with all sorts of different SSID names. I am usign the generic (internal) wifi card that came with my 1905-s301 toshiba laptop.

Is there any other software I could try? I really cannot justify putting windows on this machine just so I can browse the available wireless networks.

---

### Post by wangdang on 2006-04-03
if i remember right that toshiba has a IBM Mini-PCI Wireless NIC and uses the orinoco_pci module?

Are you getting any reaction out of it?

have you tried modprobing for it?
(modprobe orinoco_pci)

---

### Post by zapcojake on 2006-04-03
I was using an el cheapo wifi card with ndiswrapper and kwifi manager found 4 different networks in my neighborhood.  It will run under gnome or kde

---

