---
title: "display problems / gamma-contrast-brightness unusable"
date: 2010-10-16
forum: General Help
---

### Post by klapointe on 2010-10-16
Alright, I am running Maverick 10.10 on a MSI [MS-7366] motherboard. My computer is an AMD-64 bit. 

Lately I've had several problems since upgrading to 10.10. Before this I was running Karmic just fine, then I upgraded to Lucid and then upgraded to Maverick straight after. The problems began where I started up but at the boot screen it brought me to TTY1 mode and I could not start gdm. It came up as an error saying it was already running. I could only reach the desktop through recovery mode -> low graphics mode. 

When I uninstalled the Nvidia drivers I was running with some unknown driver. When turning Proprietary drivers on I could boot, but once I logged in, my screen went blank. I followed the instructions on a web page that told me how to switch to a Vesa driver, so I did that. Currently I am running Vesa [1024x768@71.0hz]. 

As soon as I have done that I have found that after I leave my computer for awhile, the display/contrast or brightness is messed up. Everything is very faded and melted in to each other. I have an attachment with a screenshot of the problem.

My xorg.conf file is:

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    HorizSync       28.0 - 73.0
   EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "vesa"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Configured Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        EndSubSection
EndSection

```It would be appreciated if the problem could be fixed without doing too much technical work- I'm more likely to screw something else up then fix this problem if that is the case. If I cannot fix this problem I will likely boot off of my Ubuntu 9.04 CD. That version has never failed to work.

Other information that may be useful: I am using a GeForce 7050 card for my display.
The only way to temporarily display normally is to restart my computer every time this happens.

---

### Post by klapointe on 2010-10-23
EDIT: This only happens when the monitor is resumed from an off or sleeping position. I can be on it using the computer for as long as I want and the display doesn't break.

Any help?

---

