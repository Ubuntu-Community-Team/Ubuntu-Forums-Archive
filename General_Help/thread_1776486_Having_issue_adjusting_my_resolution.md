---
title: "Having issue adjusting my resolution"
date: 2011-06-06
forum: General Help
---

### Post by MANi. on 2011-06-06
HELLO ALL THE PROBLEM SEEMS TO BE THAT THE LARGEST RESOLUTION I CAN SET IS 1024x768 (BUILT IN VGA CONTROLLER IS AN INTEL G33) NOW I WOULD LIKE IF ANY ONE COULD HELP ME ON THIS ISSUE THAT I COULD SET A LARGER RESOLUTION AS IN WINDOWS SEVEN I HAD 1024X1400.



NOTE: I AM TOTALLY NEW TO THIS ENVIRONMENT AS I AM A WINDOWS USER YOUR DETAILED RESPONSE WOULD BE APPRECIATED.


REGARDS,
MANi

---

### Post by seawolf167 on 2011-06-06
Welcome to the Forums

1. Click System -> Preferences -> Monitors and see if you can adjust the resolution there
2. If not, you'll want to install graphics drivers for your device, click System -> Administration -> Hardware Drivers and install any available drivers for your devices. Once that is done, repeat step #1

---

### Post by FormatSeize on 2011-06-06
> **MANi. said:**
> HELLO ALL THE PROBLEM SEEMS TO BE THAT THE LARGEST RESOLUTION I CAN SET IS 1024x768 (BUILT IN VGA CONTROLLER IS AN INTEL G33) NOW I WOULD LIKE IF ANY ONE COULD HELP ME ON THIS ISSUE THAT I COULD SET A LARGER RESOLUTION AS IN WINDOWS SEVEN I HAD 1024X1400.

When you set it to 1024X768, does it look crappy? I have a 19" wide monitor, and the resolution, theoretically, should be larger, but Slackware would only allow 1024X768 during set up, and it works fine. When I use wallpapers with higher resolutions (1600X2500), they still show up just fine with no distortion or cutting off part of the picture.
 
I'm not expert, though. Perhaps what's going on with my monitor is an exception.

---

### Post by Grenage on 2011-06-06
> **MANi. said:**
> HELLO ALL THE PROBLEM SEEMS TO BE THAT THE LARGEST RESOLUTION I CAN SET IS 1024x768 (BUILT IN VGA CONTROLLER IS AN INTEL G33) NOW I WOULD LIKE IF ANY ONE COULD HELP ME ON THIS ISSUE THAT I COULD SET A LARGER RESOLUTION AS IN WINDOWS SEVEN I HAD 1024X1400.



NOTE: I AM TOTALLY NEW TO THIS ENVIRONMENT AS I AM A WINDOWS USER YOUR DETAILED RESPONSE WOULD BE APPRECIATED.


REGARDS,
MANi

That's not uncommon; it'll be a an EDID hiccup.  You can either attempt to add a graphical mode using [xrandr]("https://wiki.archlinux.org/index.php/Xrandr"), or you can create an [xorg.conf]("http://www.grenage.com/xorg.html") config file.

---

### Post by MANi. on 2011-06-06
> **Grenage said:**
> That's not uncommon; it'll be a an EDID hiccup.  You can either attempt to add a graphical mode using [xrandr]("https://wiki.archlinux.org/index.php/Xrandr"), or you can create an [xorg.conf]("http://www.grenage.com/xorg.html") config file.


I have installed xrandr which is of no use but the highest resolution is 1024X768 which is not good. Tried Modifying the File xorg.conf which was found at the path /usr/share/xresprobe
and not at the path /etc/X11/ (xorg.conf no such file was found at the path) i have edited the one found on /usr/share/xresprobe but it is still of no use the resolution remains the same.

Looking forward for you response and already thankful to those who have replied.

---

### Post by seawolf167 on 2011-06-06
[Here is a how-to ]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")for setting display resolutions using xrandr.

[Here is a how-to ]("https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected")for configuring xorg.conf if the resolution is lower than expected. If you scroll up one section, it shows how to set the resolution using xorg.conf

---

### Post by MANi. on 2011-06-06
> **seawolf167 said:**
> [Here is a how-to ]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html")for setting display resolutions using xrandr.

[Here is a how-to ]("https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected")for configuring xorg.conf if the resolution is lower than expected. If you scroll up one section, it shows how to set the resolution using xorg.conf

ISSUE has been resolved as per the above thread XRANDR did the trick i have adjusted to the resolution of 1280X1024. 
Very much thankful for the HOWTO's. 

How ever would like to know that what caused this issue in the 1st place why wasn't i able to see the complete list of resolutions rather than only a few ??

Regards,
MANi.

---

### Post by Grenage on 2011-06-07
It tends to be down to a lack of EDID data; for a particular reason (some more obvious than others), the system doesn't get the screen information and therefore cannot give a reliable list of acceptable resolutions.

---

### Post by MANi. on 2011-06-07
> **Grenage said:**
> It tends to be down to a lack of EDID data; for a particular reason (some more obvious than others), the system doesn't get the screen information and therefore cannot give a reliable list of acceptable resolutions.

YES INDEED MY MONITOR has not been detected.

---

