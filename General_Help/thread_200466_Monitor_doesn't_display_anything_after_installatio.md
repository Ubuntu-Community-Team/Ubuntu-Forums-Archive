---
title: "Monitor doesn't display anything after installation? Fix it!"
date: 2006-06-20
forum: General Help
---

### Post by german640 on 2006-06-20
Symptoms:
You installed Ubuntu and all went well, but at restart you can see how ubuntu is loading, but at the time the graphic login window should appear, the monitor doesn't display anything and is in standby mode.

Solution:
(optionally you can connect another monitor, it probably works)
- Press Ctrl+Alt+F2 to enter console mode, or boot in recovery mode.
- Type "sudo dpkg-reconfigure xserver-xorg"
- The Xserver configuration screen will appear, the two first screens should show the brand and model of your graphics card, if not, use the VESA driver.
- After many screens (leave them with the default options) you would see one where you can select various operating modes for the monitor, DISABLE _vbe_ AND _ddc_ (Why? because these modes communicate with the monitor to retrieve information about it, it is clear that these modes are not working properly and retrieve wrong information)
- In another screen you can choose to configure the monitor with SIMPLE options, MODERATE or ADVANCED, choose ADVANCED
- In another screen you should change the frecuencies your monitor supports (in mine where horizontal: 30 - 61 and vertical: changed from 50-120 to 50-85)
- The rest of the screens with de default values.

Hope it hleps

---

