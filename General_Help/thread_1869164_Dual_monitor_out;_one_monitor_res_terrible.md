---
title: "Dual monitor out; one monitor res terrible"
date: 2011-10-25
forum: General Help
---

### Post by chris24300 on 2011-10-25
I'm running 11.04 on my laptop and I run CentOS on my desktop. Using a 30" (Dell 3007WFP) and a 24" which run proper resolution on desktop.

I hooked up my monitors to my docking station today and now my 30" doesn't go higher than 1280x800...? I tried forcing the resolution (2560x1600) but the monitor will just shut off and is disabled when I go into nvidia-settings.  I tried adding the monitor to my xorg.conf but still nothing. I have a Quadro 2000M in the laptop so this resolution shouldn't be a problem. My 24" is running at 1920x1200. 

My xorg.conf with added monitor section
[PHP]
Section "Monitor"
	Identifier "Monitor1"
	VendorName "DELL"
	ModelName  "DELL 3007WFP"
	Option	   "DPMS"
    ModeLine   "2560x1600" 268 2560 2608 2640 2720 1600 1603 1609 1646
EndSection 

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-5: NULL, DFP-1: 2560x1600 +0+0, DFP-3: 1920x1200 +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
[/PHP]

Here's a printout from the log I think is relevant
[PHP][  3594.477] (--) NVIDIA(0): Connected display device(s) on Quadro 2000M at PCI:1:0:0
[  3594.477] (--) NVIDIA(0):     DELL3007WFPHC (DFP-1)
[  3594.477] (--) NVIDIA(0):     DELL U2410 (DFP-3)
[  3594.477] (--) NVIDIA(0):     LGD (DFP-5)
[  3594.477] (--) NVIDIA(0): DELL3007WFPHC (DFP-1): 165.0 MHz maximum pixel clock
[  3594.477] (--) NVIDIA(0): DELL3007WFPHC (DFP-1): Internal Single Link TMDS
[  3594.477] (--) NVIDIA(0): DELL U2410 (DFP-3): 165.0 MHz maximum pixel clock
[  3594.477] (--) NVIDIA(0): DELL U2410 (DFP-3): Internal Single Link TMDS
[  3594.477] (--) NVIDIA(0): LGD (DFP-5): 480.0 MHz maximum pixel clock
[  3594.477] (--) NVIDIA(0): LGD (DFP-5): Internal DisplayPort
[  3594.479] (**) NVIDIA(0): TwinView enabled
[  3594.479] (II) NVIDIA(0): Display Devices found referenced in MetaMode: DFP-1, DFP-3,
[  3594.479] (II) NVIDIA(0):     DFP-5
[  3594.479] (WW) NVIDIA(0): There are only 2 heads available, trimming display device list
[  3594.479] (WW) NVIDIA(0):     from "DFP-1, DFP-3, DFP-5" to "DFP-1, DFP-3".
[  3594.515] (II) NVIDIA(0): Assigned Display Devices: DFP-1, DFP-3
[  3594.515] (WW) NVIDIA(0): Invalid display device in Mode Description "DFP-5:NULL"
[  3594.515] (WW) NVIDIA(0): Not using mode description "DFP-5:NULL"; unable to map to
[  3594.515] (WW) NVIDIA(0):     display device
[  3594.515] (II) NVIDIA(0): Validated modes:
[  3594.515] (II) NVIDIA(0):     "DFP-5:NULL,DFP-1:2560x1600+0+0,DFP-3:1920x1200+1920+0"
[  3594.515] (II) NVIDIA(0): Virtual screen size determined to be 3840 x 1200
[  3594.742] (WW) NVIDIA(0): Cannot find size of first mode for DELL3007WFPHC (DFP-1);
[  3594.742] (WW) NVIDIA(0):     cannot compute DPI from DELL3007WFPHC (DFP-1)'s EDID.
[  3594.742] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[  3594.742] (WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
[  3594.742] (WW) NVIDIA(0):     UBB.[/PHP]

---

### Post by chris24300 on 2011-10-26
Nobody else has experienced this? No ideas?

---

