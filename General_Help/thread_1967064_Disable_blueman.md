---
title: "Disable blueman"
date: 2012-04-27
forum: General Help
---

### Post by Finalfantasykid on 2012-04-27
My laptop does not have bluetooth, so how do I go about disabling the blueman-applet from showing up?  I have disabled bluetooth service from the Startup Applications, but that has done nothing.

---

### Post by Finalfantasykid on 2012-04-27
It is off (see screenshot)

---

### Post by mode7 on 2012-04-27
I think it is *supposed* to automatically hide if no bluetooth adapter is detected.
Either way, you can enter "gksu nautilus /etc/xdg/autostart" into a terminal, then delete bluetooth-applet.desktop and bluetooth-applet-unity.desktop.
You probably will want to back them up first. That works in 11.10, I imagine in 12.04 as well..

---

### Post by Finalfantasykid on 2012-04-27
> **poonjabi said:**
> just uninstall it in synaptic

Thanks that did it!

---

