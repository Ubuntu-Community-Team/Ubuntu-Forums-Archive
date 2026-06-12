---
title: "No sound!! Help"
date: 2009-08-16
forum: General Help
---

### Post by philtheman0901 on 2009-08-16
I currently just installed ubuntu 9.04 and have installed all the updates. I try to use vlc and stream music online and i get NO sound through my speakers. I have a basic sound card installed that came with my xp. I don't know what it is called. I have tried opening alsamixer but nothing appears and myt speakers are not on mute either. PLEASE HELP!

---

### Post by warp99 on 2009-08-16
When you boot from the install disk does the sound work?

---

### Post by philcamlin on 2009-08-16
please post output of 

 ```
lspci
```

---

### Post by philtheman0901 on 2009-08-17
These are the results that erminal give me:

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0f.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
00:10.0 Ethernet controller: Linksys, A Division of Cisco Systems WMP11v4 802.11b PCI card
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)


I know that the last 3 on the list obviusly is not my sound card.

---

