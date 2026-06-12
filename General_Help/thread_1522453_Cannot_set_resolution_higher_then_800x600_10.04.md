---
title: "Cannot set resolution higher then 800x600 10.04"
date: 2010-07-02
forum: General Help
---

### Post by ally_uk on 2010-07-02
Hi guys I have just done a clean install of 10.04 and cannot for the life of me set the resolution higher then 800x600 

When I go to change the resolution I am greeted with a unknown monitor.

lspci | grep -i vga 

 VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 01)

Here is the Xorg config file I have configured


Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 16
Subsection "Display"
Viewport 0 0
Depth 16
Modes "1280x800" "1024x768" "800x600"
EndSubSection
EndSection


Many Thanks

---

### Post by dino99 on 2010-07-02
maybe an issue with VIA chipset

anyway, actual kernel deal directly with X, so no need of xorg.conf

sudo rm -f /etc/X11/xorg.conf

open synaptic repo and add this ppa:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

then update, upgrade

reboot and then check if yhe driver is activated: system admin hardware driver

---

### Post by SmokeyThePanda on 2010-07-02
I am not an expert on this topic, but in the past, I have dealt with resolution problems after pretty much every clean install. I'm pretty sure the things you need to add are the Horizontal Sync and Vertical Refresh. These can both be found in your monitors manual or a page online that lists your monitor's specs. 

Here is what mine looks like. You can use it as a guide and add the options to make it specific to your monitor.


[PHP]Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    HorizSync     30 - 60
    VertRefresh   60 - 75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Configured Video Device"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
[/PHP]

---

### Post by ally_uk on 2010-07-02
Thank you guys the first solution wouldn't let me add the link to the repositories, 

Panda your solution worked did a reboot and was able to up the resolution :) 

solved!

---

### Post by SmokeyThePanda on 2010-07-02
Cheers mate. I'm glad I could help, even though I am a noob at linux. :p

---

