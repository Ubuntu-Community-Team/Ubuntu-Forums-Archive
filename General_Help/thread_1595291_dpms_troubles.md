---
title: "dpms troubles"
date: 2010-10-13
forum: General Help
---

### Post by dillzz on 2010-10-13
Hoping someone can help.

I have 3 Dell monitors in this order. (#1) 24" U2410, (#2) 24" 2408wfp, (#3) 24" U2410. I have a 9600gt with the first output going to monitor 1, the second output is going to a triple head to go then connects both monitors #2 and #3 up. 

I had this setup before but had two budget panels for monitors #1 and #3. (Dell e248wfp) I recently upgraded through an RMA process and recieved these much nicer ones . However monitor #3 will not enter a into powersave mode. I have swapped it out and same behavior. 

Below is my xorg.conf. I am running Kubuntu 10.10 x86_64 with nvidia driver 260.19.06. The only items that have changed was going to Kubuntu 10.04 to 10.10 and upgrading nvidia drivers, and two monitors . Any one have an idea as to what could be causing this, or what part of the upgrade I should start troubleshooting? 

Testing it with: xset dpms force off


Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen0" 0 0
EndSection

Section "Module"
Load "glx"
EndSection

Section "Monitor"
Identifier "Monitor0"
ModeLine "1920x1200" 154.00 1920 1968 2000 2080 1200 1203 1209 1235 +HSync +HSync
ModeLine "3840x1200" 308.00 3840 3904 3968 4160 1200 1203 1213 1235 +HSync +VSync
HorizSync 30-83
VertRefresh 56-76
EndSection

Section "Device"
Identifier "Videocard0"
Driver "nvidia"
VendorName "Leadtek"
BoardName "9600GT"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
Option "UseEDID" "False"
Option "ExactModeTimingsDVI" "True"
Option "NoLogo" "True"
Option "TwinView" "True"
Option "TwinViewOrientation" "RightOf"
Option "TwinviewXineramaInfo" "True"
Option "TwinViewXineramaInfoOverride" "1920x1200+0+0, 1920x1200+1920+0, 1920x1200+3840+0"
Option "DynamicTwinView" "False"
Option "MetaModes" "1920x1200,3840x1200"
Option "SecondMonitorHorizSync" "30-83"
Option "SecondMonitorVertRefresh" "56-76"
SubSection "Display"
Viewport 0 0
Depth 24
Modes "3840x1200"
EndSubSection
EndSection

---

### Post by dillzz on 2010-10-17
bump

---

