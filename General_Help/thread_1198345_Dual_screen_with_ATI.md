---
title: "Dual screen with ATI"
date: 2009-06-27
forum: General Help
---

### Post by nsblenin on 2009-06-27
I put a secondary screen in my video card. In the screen apears the same (mirror) than in principal screen. I want to expand the desktop horitzonally.
I tried to add this in xorg.conf but nothing changes. Even the resolution of the secondary is 1024x768 like the first and i can't change it.

Option "MergedFB" "true" #Enable MergedFB function
  Option "MonitorLayout" "CRT, TMDS" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
  Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  Option "OverlayOnCRTC2" "true"
  Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  Option "MetaModes" "1024x768-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"

---

