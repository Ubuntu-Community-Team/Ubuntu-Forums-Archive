---
title: "xorg.conf and logitech trackman marble mouse"
date: 2011-11-21
forum: General Help
---

### Post by linuxhippy on 2011-11-21
I just bought a Logitech trackman marble mouse.  It has 4 buttons and a finger marble.  I googled around and found this can be programed to work in Linux using the xorg.conf file.  A scroll can even be simulated. Where would I put this in Ubuntu 11.10 since I see there is a directory now at /usr/share/X11/xorg.conf.d

Here is what I need to put into an xorg.conf file:

#       - - - Logitech Marble Mouse Settings - - -
#
#       For the sake of comments below, a Logitech Marble Mouse has buttons
#       labeled from left to right: A (large), B, C, D (large). 

#       Preferred options for right-handed usage are:
#       Left to right:  A=1,normal click  B=2,middle-click  C=2,middle-click  D=3,right-click
#       Press button B (hold button while rolling trackball) to emulate wheel-scrolling. 

#       Preferred options for left-handed usage (saying 'alternate-click' instead of 'right click'):
#       Left to right:  A=3,alternate-click  B=2,middle-click  C=2,middle-click  D=1,normal click
#       Press button C (hold button while rolling trackball) to emulate wheel-scrolling.

#       The trackball can scroll in two-axes, unlike a typical wheel mouse. Adjust the
#       settings to constrain the scroll action to vertical-axis-only if you prefer.

#       Pressing both large buttons simultaneously (b) produces a "back" action (=8). Finally,
#       pressing and holding button B while rolling the trackball emulates wheel-rolling action.

Section "InputClass"
        Identifier  "Marble Mouse"
        MatchProduct "Logitech USB Trackball"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
#       Physical button #s:     A b D - - - - B C    b = A & D simultaneously;   - = no button
        Option "ButtonMapping" "1 8 3 4 5 6 7 2 2"
#       Option "ButtonMapping" "1 8 3 4 5 6 7 2 2"   #  For right-hand placement
#       Option "ButtonMapping" "3 8 1 4 5 6 7 2 2"   #  For left-hand placement
#
#       EmulateWheel refers to emulating a mouse wheel using Marble Mouse trackball.
        Option "EmulateWheel" "true"
#       Option "EmulateWheelButton" "8"              # Factory default; use "9" for left-side placement.
        Option "EmulateWheelButton" "8"
#       Option "ZAxisMapping" "4 5"
        Option "ZAxisMapping" "4 5"
#       Option "XAxisMapping" "6 7"                  # Disable this for vertical-only scrolling.
#       Option "XAxisMapping" "6 7"
#       Emulate3Buttons refers to the act of pressing buttons A and D
#       simultaneously to emulate a middle-click or wheel click.
        Option "Emulate3Buttons" "true"
#       Option "Emulate3Buttons" "true"              # Factory default.
EndSection

---

