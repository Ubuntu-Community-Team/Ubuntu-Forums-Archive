---
title: "mx1000 button issues"
date: 2010-06-05
forum: General Help
---

### Post by patsissons on 2010-06-05
i am having an issue with my mx1000 that doesn't seem to fall into any of the other common mx1000 issues.

My issue is that two of my buttons are not registering at all with evdev.  Button 3 (mouse wheel click) and button 7 (mouse wheel right).  I can verify that all other buttons are functioning as expected:
1  : Left Click
3  : Right Click
4  : Mouse Wheel Forward
5  : Mouse Wheel Backwards
6  : Mouse Wheel Left
8  : Thumb Back
9  : Thumb Forward
10 : Thumb Middle
11 : Cruise Forwards UP
12 : Cruise Backwards UP

my xorg mouse section is below.
```
Section "InputDevice"
    Identifier     "MX1000"
    Driver         "evdev"
    Option         "Name" "Logitech USB Receiver"
#    Option         "HWHEELRelativeAxisButtons" "7 6"
    Option         "Buttons" "12"
#    Option         "ZAxisMapping" "11 12 10 9"
    Option         "GrabDevice" "true"
EndSection
```

I plan on debugging this issue for the next while, so i'll post any other details i come across.

---

### Post by patsissons on 2010-06-05
the GrabDevice option was just an attempt to fix things, it didn't work and may be ignored.

I think this bug report describes my problem quite well:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/443284](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/443284)

I wonder if it has anything to do with the Macintosh mouse button emulation device that is loaded (which is why i tried GrabDevice option).  I hope that those two buttons are not getting diverted to the wrong device.

P.S. i guess i should mention that i am on karmic (kubuntu).

---

### Post by patsissons on 2010-06-05
Semi good news, i have an actual solution.  seems this is a hardware issue, and talking to a friend of mine with the same mouse it is somewhat common. The middle mouse button (2) is just a bad button, i gave it some extra hard pushes (after taking the mouse apart) and now button 2 works again.  Sadly, button 7 is still dead, but it is much more insignificant in daily use.

So for anyone who experiences this issue, it is very possible that your mouse is just dead.

FYI, i disabled all input sections in my xorg.conf file, the mx1000 is detected naturally by hal/evdev.

---

