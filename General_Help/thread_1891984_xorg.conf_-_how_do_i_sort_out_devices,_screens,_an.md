---
title: "xorg.conf - how do i sort out devices, screens, and monitors?"
date: 2011-12-07
forum: General Help
---

### Post by RageLtMan on 2011-12-07
I have a laptop with a pair of ATI GPU's in it - 6970m MXM cards.  I'm running 11.04 and it cannot detect the second card unless they are in crossfire mode which is very flaky (drivers most likley, computational errors occur in second GPU).  When fglrx intitially configures xorg.conf with aticonfig --adapter=all -f --initial, it creates separate sections for each device, creates a monitor for each device, and a screen for each device.  Problem is, there's only one monitor - the LVDS panel on the laptop.  When this default configuration is launched, X does not start as the two devices apparently fight over which one gets the panel.   If i disable the second screen, i can start X, but all applications only see one GPU (clinfo etc).  How can i map both devices to one screen, or how can i get X to understand that the second GPU does exist, but is not mapped to an output?

---

