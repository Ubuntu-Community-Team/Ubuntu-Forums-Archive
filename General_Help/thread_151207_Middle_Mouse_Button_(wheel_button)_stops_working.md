---
title: "Middle Mouse Button (wheel button) stops working"
date: 2006-03-27
forum: General Help
---

### Post by xbruceyx on 2006-03-27
Hi folks,

I did some thread searching and couldn't find a solution to my problem.
For quite some time, my mouse worked perfectly. Now this is my problem: the middle mouse button with the wheel scrolls up and down fine but when pressed does not work. In the past, when pressed it would work wonders when doing repetitive copying and pasting and/or opening links as new tabs in firefox. This is  just plain annoying.

Here is my /etc/X11/xorg.conf mouse section:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Buttons"               "5"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
EndSection


Changing "Emulate3Buttons"       "false" to "true" has no effect.
Hardware is a usb wireless mouse and keyboard combo.

Any ideas? Thanks.

-Bruce

---

### Post by jerrykenny on 2006-03-27
Should Emulate 3 Buttons not be set to true ?

---

### Post by AndrewCaul on 2006-03-27
If I recall correctly, a mouse wheel counts as two buttons.

---

### Post by xbruceyx on 2006-03-28
5 = Left Click, Right Click, Scroll Wheel Up, Scroll Wheel Down, Scroll Wheel Click

---

### Post by tonysohn on 2007-03-10
Try changing "ImPS/2" to "ExplorerPS/2"

---

