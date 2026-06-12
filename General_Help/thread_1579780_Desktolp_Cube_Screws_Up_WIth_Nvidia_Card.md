---
title: "Desktolp Cube Screws Up WIth Nvidia Card"
date: 2010-09-22
forum: General Help
---

### Post by gallifrey on 2010-09-22
Hi, 
   I am running a fresh install of 10.04 with Nvidia-Current proprietary drivers for a GeForce 9600 GT. Everything seems fine, initially, until I enable desktop cube. Then my window borders disappear. If I reboot, I am left with a blank desktop with no panels, no windows, nothing. Right clicking has no effect. 

I have tried reinstalling Compiz and plugins, but it made no difference. 

Here is the output of lshw -C display:
> 
  *-display               
       description: VGA compatible controller
       product: G96 [GeForce 9600M GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff(prefetchable) memory:d0000000-d1ffffff ioport:6000(size=128)
 

I also ran the compiz-check script by forlong, but that did not reveal any problems. 

Any suggestions would be most appreciated! :)

---

### Post by Quackers on 2010-09-22
If you've got Cairo Dock click on the Compiz icon and then click on Reload WM 
If not, go to Applications > System Tools > Compiz Fusion Icon and click it. The icon should then appear in your top bar. Right-click the icon and then click on Reload Window Manager.

Any good?

---

### Post by gallifrey on 2010-09-22
> **Quackers said:**
> If you've got Cairo Dock click on the Compiz icon and then click on Reload WM 
If not, go to Applications > System Tools > Compiz Fusion Icon and click it. The icon should then appear in your top bar. Right-click the icon and then click on Reload Window Manager.

Any good?

Gave it a go, but no good. The window manager reloaded, but there were still no window borders. I have re-enabled desktop wall for now, as if I reboot with the cube, I will have no desktop!!! 

Thanks for your input though.

Any other ideas??

EDIT: After disabling Desktop Cube, and reloading WM, the window borders came back. Still leaves me cubeless though! :(

---

### Post by Quackers on 2010-09-22
To be honest I gave up trying to use the cube. I never got it working at all. I have a nvidia 8600M GT card. You could try rolling back the video driver to the one before the current one - I did that to overcome one or two  little niggles.

---

### Post by gallifrey on 2010-09-22
> **Quackers said:**
> To be honest I gave up trying to use the cube. I never got it working at all. I have a nvidia 8600M GT card. You could try rolling back the video driver to the one before the current one - I did that to overcome one or two  little niggles.

:) Beat you too it. I regressed the driver back to the previous one, and the one prior. The cube just doesn't want to play ball :). I also tried using emerald instead of GTK as my window decorator, but it made no difference. I am truly at a loss.

---

### Post by Quackers on 2010-09-22
Sadly, so am I :-( 
Maybe someone will come up with something better soon.

---

