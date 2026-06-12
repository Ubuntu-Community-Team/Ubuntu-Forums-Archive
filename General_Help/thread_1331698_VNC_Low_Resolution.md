---
title: "VNC Low Resolution"
date: 2009-11-19
forum: General Help
---

### Post by kazbear on 2009-11-19
I have Ubuntu 9.10 on a box that I remote into using VNC.  The box does not have a mouse, keyboard or monitor.  Since the upgrade, when I VNC into the box, the resolution is 640x480, with no other options except 320x240.

The computer has an Nvidia card and I am using the driver from the Hardware Driver list.  When I look at the options in that panel, it is set to "Auto".

So, I rebooted with a monitor attached.  Now I have the higher resolutions.  I set the Nvidia driver to 1280x1024 instead of auto and rebooted with out the monitor.  Connecting with VNC gave me the higher resolution.  All good.

However, after sutdown, and reboot again, its back to 640x480.

How do I force it to the higher resolution and keep it that way?

Thanks

---

### Post by nikgare on 2009-11-19
I have the same setup.
I changed the xorg file so that X now uses the vesa driver, and also specified the resolution.  This works great for me - here is my xorg.conf file:
```

Section "Device"
        Identifier      "Configured Device"
        Driver  "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 31-61  
        VertRefresh 50-75
        Modeline "1024x768" 25.20 640 688 784 800 350 410 412 449
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Device"
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection


```

---

