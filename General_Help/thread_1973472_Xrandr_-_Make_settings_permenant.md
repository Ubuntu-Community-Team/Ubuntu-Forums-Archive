---
title: "Xrandr - Make settings permenant"
date: 2012-05-04
forum: General Help
---

### Post by lakerssuperman on 2012-05-04
I am running a Radeon 4650 with the OSS drivers on Ubuntu 11.10.  I have it hooked to a 32 inch LCD tv.  The tv is el cheapo and doesn't report it's information properly leading to overscan and the picture going beyond the boundaries of the tv.  I have successfully gotten the picture to fit the screen using:

xrandr HDMI-0 --set underscan on --set "underscan hborder" XX --set "underscan vborder" XX

However, these settings are wiped away upon reboot.  I would like to make them permenant and have them take effect before the display mananger and login screen come up.  So far I have only gotten them to affect my actual desktop session by placing the above command in the Lightdm config file.  Can I just place it in my xorg.conf or does the format need to be altered for the xorg.conf file?

Where should I place this command so that everything including the login screen have the proper dimensions?  Thank you for your help.

---

