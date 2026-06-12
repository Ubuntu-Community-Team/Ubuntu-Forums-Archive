---
title: "Screen goes dark - Screensaver &amp; Power settings are all on"
date: 2010-01-29
forum: General Help
---

### Post by LuridCinema on 2010-01-29
My monitor(s) are going black no screensaver startup, just black after a few minutes of inactivity and I have checked to make sure my screensaver is turned off and the settings on Power Mgmt is always on ??? whassup ?? I cannot watch movies or videos w/o interruption anymore

---

### Post by LuridCinema on 2010-01-29
Fixed the issue w/ the below, 
------------------------------------------------------------------------------
Are you using XGL & Ati card? In that case it's a known bug, and to get rid of it add the following section to /etc/X11/xorg.conf:

Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection

---

