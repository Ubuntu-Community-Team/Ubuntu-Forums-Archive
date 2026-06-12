---
title: "Restore xorg.conf"
date: 2010-01-16
forum: General Help
---

### Post by thepalm2 on 2010-01-16
I was previously using fglrx as a video driver on my Ati 4850.  I am now running dual monitors and the configuration was not able to get that set up correctly.  
I followed the instructions at [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) to install the open source driver.  However, Xorg didn't come up on a reboot, so I replaced xorg.conf with xorg.conf.failsafe.

The screens now work however, I cannot work out how to write a new xorg.conf which uses the radeon driver, I have tried:
    dpkg-reconfigure xserver-xorg
but this did nothing

Current xorg.conf:
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"

Any help getting the open source ATI driver working?

---

