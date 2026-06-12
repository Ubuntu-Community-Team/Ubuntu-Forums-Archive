---
title: "Display not updating on new install (Newbie!)"
date: 2010-01-21
forum: General Help
---

### Post by Goodychrischild on 2010-01-21
Hello all, here's my first post on this forum!

I have just installed 9.10 on an old Dell C610 laptop as I had to install a new hard drive and didn't have the old XP licence number or COA!

Anyway, the Ubuntu install all seemed to go ok but I'm having a major problem with the display not following what I'm doing and not updating as windows are opened and closed. Am I likely to be doing something silly or have I got a hardware conflict somewhere. Where should I start?

Thanks,
Chris

---

### Post by Goodychrischild on 2010-01-21
Should I have installed an older version of Ubuntu? :confused:

Chris

---

### Post by jhwangus on 2010-02-15
Hi,

My C610 with Ubuntu 8.10 was working fine.  I upgraded it to Ubuntu 9.10 last night and I encountered the same problem as you described.  The desktop was not updated correctly.

After googling around and toying with it this afternoon, I have made it working.  Here is my summary:

1. Dell C610 uses various ATI Radeon Mobility video cards (mine is Mobility M6 LY).  You can check yours using lspci command at a terminal.

2. Ubuntu comes with two kinds of ATI video drivers.
    fglrx - ATI Inc. private driver as a part of ATI Catalyst
    ati (radeon) - Open source ATI driver
    
Ubuntu 8.10 has fglrx driver from Catalyst 9.3.  Ubuntu 9.10 has Catalyst 9.4+.  ATI stopped to support the older video cards in Catalyst 9.4+.  However, you can not use the driver in Catalyst 9.3 with Ubuntu 9.10 unless you want to downgrade your kernel and X server to the older versions.  So the only choice is to use the open source driver.

3. During my upgrade (and your installation), it's probably configured to use fglrx.

4. I used the following commands to completely uninstall fglrx and reinstall ati.

[http://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](http://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

5. Since my ATI Mobility M6 only has 16 MB RAM, I edit the xorg.conf to set the color depth to 16, as well as setting some options that makes the performance a little better.

sudo vim /etc/X11/xorg.conf

Section "Device"
    Identifier    "ATI Radeon M6"
    Driver        "ati"
    Option        "AGPSize" "32"
    Option        "XAANoOffscreenPixmaps" "on"
    Option        "AGPMode" "4"
    Option        "AGPFastWrite" "on"
    Option        "DisableGLXRootClipping" "on"
    Option        "AddARGBGLXVisuals" "on"
    Option        "AllowGLXWithComposite" "on"
    Option        "EnablePageFlip" "on"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "ATI Radeon M6"
    DefaultDepth    16

    SubSection "Display"
        Depth    8
        Modes    "1024x768"
        Virtual    1024 768
    EndSubSection
    SubSection "Display"
        Depth    16
        Modes    "1024x768"
        Virtual    1024 768
    EndSubSection
EndSection

Section "DRI"
    Mode        0666
EndSection

Section "Extensions"
    Option        "Composite" "Enable"
EndSection

6. Reboot and then everything is fine!

Hope this would be helpful to you.

Jack

---

