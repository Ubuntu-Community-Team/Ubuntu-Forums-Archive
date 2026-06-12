---
title: "Dual Monitor catch 22"
date: 2011-06-24
forum: General Help
---

### Post by imaca on 2011-06-24
Hi,
I have an Acer Aspire 5253 (AMD E-350) hooked up by hdmi to a samsung TV.
Initialy the displays were cloned but after setting to multi-display (which works)using Catalyst control centre the system locks up if I try to change back, or set to a single display. The login dialogue comes up on the TV, so I can't log in without it (system locks up if hdmi unplugged) 
I can boot up in basic graphics mode, but can't use the Catalyst control centre to change settings.
Any ideas how to recover?:confused:

---

### Post by dino99 on 2011-06-24
is it something new related to package(s) upgrade ?
maybe you can try with different versions (from xorg-edgers for example)

but you should directly ask on launchpad with all the necessary hardware info (dmidecode/lspci -vvnn)

or report against cccs

---

### Post by LordNeo on 2011-06-24
Have you tried to unplug the TV and then try to switch modes using the keyboard shortcuts?

by default every notebook has some "func" key + something else to switch between "Extended Desktop", "Mirror", "whateverothermode"

---

### Post by imaca on 2011-06-30
> **dino99 said:**
> is it something new related to package(s) upgrade ?
maybe you can try with different versions (from xorg-edgers for example)

but you should directly ask on launchpad with all the necessary hardware info (dmidecode/lspci -vvnn)

or report against cccs
Um, not sure what you mean.
Managed to get the login back on the laptop screen.
Anyway, if I boot in recover mode and choose "create new graphics configuration" or just "restart x" it starts perfectly.
Cannot boot normally, it either locks before the login screen, or less commonly , immediately after.

---

