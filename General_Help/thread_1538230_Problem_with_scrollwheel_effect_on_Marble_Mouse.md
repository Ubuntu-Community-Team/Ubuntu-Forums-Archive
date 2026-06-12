---
title: "Problem with scrollwheel effect on Marble Mouse"
date: 2010-07-24
forum: General Help
---

### Post by gufy78 on 2010-07-24
Hi there

I know there was few threads about it but I have still some confusions.

I am trying to set up small buttons of my Logitech Marble Mouse in Ubuntu 10.04
and despite spending 2 days on it I am still not satisfied.

I read there are couple of solutions there but these simply DO NOT work for me:

1)  editing xorg.conf  - I tried similar combinations but these do not do anything
apart from freezing my machine on the start

Section "InputClass"
        Identifier  "Marble Mouse"
        MatchProduct "Logitech USB Trackball"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "ButtonMapping" "1 8 3 4 5 6 7 2 9"
        Option "EmulateWheel" "true"
        Option "EmulateWheelButton" "9"
        Option "ZAxisMapping" "4 5"
        Option  "XAxisMapping" "6 7"
        Option  "Emulate3Buttons" "false"
EndSection


2) creating /etc/hal/fdi/policy/10-marblemouse.fdi[FONT=monospace] 

[/FONT]<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
    <match key="info.product" string="Marble Mouse (4-button)">
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
  </device>
</deviceinfo>

[FONT=monospace]It seems NOT doing anything, no scroll effect at all,
Tried to swap  strings  4 5 6 7   with  8 and 9 (small buttons) - no effect


3)  the only solution that helped was creating .Xmodmap with this:
[/FONT]
! Logitech USB Marble Mouse Physical buttons available: 
!  Mouse Big:   1 3
!  Mouse Small: 8 9
! Xmodmap positional meanings:
!  Pointer: Left-click, Middle-click, Right-click, Scroll-up, Scroll-down, Scroll-left, Scroll-right, Scroll-click, 9
pointer = 1 9 3 4 5 6 7 8 2

I gives me autoscroll, at least

In windows I had however set up small left button as Scroll-down and small right button as Scroll-up
and I got used to that. When I set it up by 'pointer' it is not perfect as buttons do not repeat itself, I cannot change number of line to scroll etc.

Can anyone explain me how to set it up perfectly


Many thanks
guFy

---

