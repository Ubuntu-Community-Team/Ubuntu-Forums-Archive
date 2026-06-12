---
title: "Dual Screen"
date: 2009-08-31
forum: General Help
---

### Post by BarefootSoul83 on 2009-08-31
ok then: I'm running Ubuntu Jaunty-J ...... I had dual screen working great a couple months ago...I had to go in: *gksudo* gedit /etc/X11/*xorg*.conf

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
        Virtual    2720 1282
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "intel"
#    Driver        "vesa"
EndSection


........ as you can see I changed the driver to "intel" for that is what my Toshiba Satellite has integrated with it.  

Now, whenever I try to hook up an external monitor to have dual screens...the best setting will give me a perfect laptop screen and only half a screen on the external monitor.  Whats up with that?  

Once this is fixed I would also like to be directed on how to setup the startup  files (i guess) to have 2 settings...(one for only laptop...the other for dual screen...)

Thanks!

---

### Post by BarefootSoul83 on 2009-09-06
bump

---

