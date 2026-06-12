---
title: "save GPU fan speed"
date: 2011-07-18
forum: General Help
---

### Post by karlalbury on 2011-07-18
Ubuntu 11.4 natty 64bit

edited: etc/x11/xorg.config and added cool bits option 4 i now have fan control in **nvidia-settings** tried saving but the fan reverts on reboot
problem is i have to set it each time i start ubuntu is there a way to save this setting so say fan is set to 85% at login?

Card: GeForce 9800 GTX

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX/9800 GTX+"
**    Option "Coolbits" "4"**
EndSection

thanks in advance, Karl

---

