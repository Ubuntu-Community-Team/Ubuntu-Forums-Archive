---
title: "vga16fb: not registering due to another framebuffer present"
date: 2011-02-17
forum: General Help
---

### Post by Sanji_ on 2011-02-17
Sorry if my thread not post in right room. I'm still new in this forum.

When I'm working with eclipse PDT, my screen gone blank. I have to force my netbook to restart. After that I check the the log, and here's the log:

```
Feb 17 23:03:17 qzuma kernel: [   17.138069] fb0: inteldrmfb frame buffer device
Feb 17 23:03:17 qzuma kernel: [   17.138076] registered panic notifier
Feb 17 23:03:17 qzuma kernel: [   17.149074] acpi device:20: registered as cooling_device2
Feb 17 23:03:17 qzuma kernel: [   17.149969] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
Feb 17 23:03:17 qzuma kernel: [   17.150103] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
Feb 17 23:03:17 qzuma kernel: [   17.150157] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Feb 17 23:03:17 qzuma kernel: [   17.166028] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 17 23:03:17 qzuma kernel: [   17.207552] vga16fb: mapped to 0xc00a0000
Feb 17 23:03:17 qzuma kernel: [   17.207563] vga16fb: not registering due to another framebuffer present
Feb 17 23:03:18 qzuma kernel: [   17.356908] input: HDA Intel Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Feb 17 23:03:18 qzuma kernel: [   17.357140] input: HDA Intel HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Feb 17 23:03:18 qzuma kernel: [   17.416575] [drm] Big FIFO is enabled
Feb 17 23:03:18 qzuma kernel: [   17.416595] [drm] Big FIFO is enabled
Feb 17 23:03:18 qzuma kernel: [   17.457150] Console: switching to colour frame buffer device 128x37
Feb 17 23:03:18 qzuma kernel: [   17.467099] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
```Does anyone know what happened with my netbook??
Could you explain to me!! :p thanks b4

---

