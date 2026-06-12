---
title: "Prob connecting Acer Revo to TV"
date: 2010-12-29
forum: General Help
---

### Post by Termi11 on 2010-12-29
Hello all,

i have a problem connecting my Acer Revo to my LG 32LD350 TV.
I installed the nvidia modules and vdpau for xbmc.
Installed Ubuntu 10.10 32 bit.

After the modules where installed, gdm starts fine, sound ok, but after +-10 seconds i get a black screen.

Then i added the modelines from this documentation:
[http://forum.xbmc.org/showthread.php?t=54685](http://forum.xbmc.org/showthread.php?t=54685)

> HorizSync       30.0 - 83.0
    VertRefresh     58.0 - 62.0
    ModeLine       "1920x1080" 138.80 1920 1968 2000 2080 1080 1083 1088 1111 +hsync
    ModeLine       "1360x768" 72.0 1360 1408 1440 1520 768 771 781 790 +hsync -vsync


Nothing helped.
After each restart gdm starts for +-10 seconds.
Only when i add the 
Option "UseEdid" "FALSE"
Parameter to xorg.conf, the picture remains ok, but i have no sound anymore.

In the xorg log are no error messages. Only this:

> [   680.560] (WW) NVIDIA(0): The EDID for LG Electronics LG TV (DFP-0) contradicts itself:
[   680.560] (WW) NVIDIA(0):     mode "1920x1080" is specified in the EDID; however, the
[   680.560] (WW) NVIDIA(0):     EDID's valid VertRefresh range (58.000-62.000 Hz) would
[   680.560] (WW) NVIDIA(0):     exclude this mode's VertRefresh (25.0 Hz); ignoring
[   680.560] (WW) NVIDIA(0):     VertRefresh check for mode "1920x1080".


I also tried with the following parms:

Option "UseEDIDFreqs" "FALSE"
Option "UseEDIDDpi" "FALSE"

then i have sound, but no picture.

What else could be wrong?

Thanks

---

