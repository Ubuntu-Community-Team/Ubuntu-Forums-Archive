---
title: "GSynaptics error message"
date: 2006-02-20
forum: General Help
---

### Post by issueperson on 2006-02-20
Hey All,
i'm running breezy on a latitude D610. I've managed to get most of the features configured, but i can't get the darned touchpad to scroll.
I've followed the directions on other posts to get it working, no luck.
I also installed GSynaptic and have gsynaptic-init run at boot. when i try to adjust the settings on the applications > system > preferences > touchpad menu i get the following error message.
-----------------------------
"GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"
----------------------------
But the thing is, i have SHMConfig set to true in my xorg.conf.
my USB mouse and touchpad section of xorg.conf is as follows (the bottom one is the touchpad that i'm trying to get to scroll vertically, preferably using gsynaptics if it'll work):

-------------------------------------------
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
EndSection
---------------------------------------

Let me know if you can help. Thanks
issueperson

---

