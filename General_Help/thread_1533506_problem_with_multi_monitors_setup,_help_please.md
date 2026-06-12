---
title: "problem with multi monitors setup, help please"
date: 2010-07-18
forum: General Help
---

### Post by NoirTree on 2010-07-18
Hi all, 

Fresh to Linux, need information on how to setup the system with 3 monitors using 2 graphics.

ATI Radeon RV730 Pro AGP- with (2) DVI ports
ATI Radeon RV100 QY PCI- with (1) DVI and (1) VGA

Currently I have the system setup as...

monitor (1), RV730 DVI port, Position 0 0, 1360x768
monitor (2), RV730 DVI port, RightOf monitor (1), 1440x900
monitor (3), RV100 VGA port, Right of monitor (2), 1440x900

however, multihead on RV730 stretches the full screen video or anything full screen to monitor(2), kind of like NVidia's Twinview, If I maximized a window – it would stretch across both monitors.

in xorg,conf, I have disable Xinerama already.  I am using opensource and done many experiences to come up with a solution until now.  I am stuck. 

Here's the Device section for my radeon 4650 card, using multihead.

Section "Device"
        Identifier      "radeon HD4650"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps" "true"
        Option         "AGPFastWrite" "yes"
        Option         "RenderAccel" "on"
        Option          "monitor-DVI-0" "AOC"
        Option          "monitor-DVI-1" "Samung"
EndSection

Section "ServerLayout"
        Identifier      "tri view"
        Screen      0   "ScreenA" 0 0
    Screen      1   "ScreenS" RightOf "ScreenA"
    Screen      2   "ScreenH" RightOf "ScreenS"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "Xinerama" "0"
    option             "Clone" "0"
EndSection


question#1:
How can I disable multihead in xorg.conf?

question#2:
How can I set each monitor as independent monitor instead having the 'stretched' effect?

I have a 32" LCD TV as monitor(1) with 19" WS monitor as monitor(2).  The combined 'stretch' effort when playing full screen video is just too much for my eyes. 

Please help if you may have the answer.  Thanks! ;)

---

### Post by Sm0ke42o on 2010-07-18
Same issue here. Tried a number of fixes to no avail.

---

### Post by NoirTree on 2010-07-18
there are (2) ways that might make it work... haven't tried it.

1. 
divide the RV730 video card into two BUSID, PCI:1:0:1 and PCI:1:0:1
(haven't test to see if that's possible) :confused:

2. use multi-user for each video card, which would still give me control over 3 monitors, but would require an additional keyboard and mouse, plus have to login twice:mad:

any feedback on this subject would be appreciated. thx!

---

### Post by schmolch on 2010-07-18
Im not familiar with radeon cards/drivers but how is it supposed to work without Xinerama?

---

