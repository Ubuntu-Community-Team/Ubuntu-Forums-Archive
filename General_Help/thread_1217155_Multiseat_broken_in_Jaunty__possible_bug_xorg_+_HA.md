---
title: "Multiseat broken in Jaunty / possible bug xorg + HAL"
date: 2009-07-19
forum: General Help
---

### Post by Wolfgang.Klein on 2009-07-19
Hello!

I am using a multiseat machine running on Hardy and I'd like to upgrade that machine to Jaunty. Unfortunately, there seems to be a bug that causes xorg to add USB devices although I told it not to use HAL:

```
Section "ServerFlags"
    Option      "DontVTSwitch"
    Option      "HandleSpecialKeys"     "Always"
    Option      "AllowMouseOpenFail"  "true"
    Option      "DontZap"                   "Off"
    Option      "AllowEmptyInput"       "false"
    [COLOR=Red]**Option     "AutoAddDevices"    "false"**[/COLOR]
EndSection
```The following devices are attached to the machine: 1 USB keyboard, 1 PS/2 keyboard, 2 USB mice. When I start X, the mice work independently and the PS/2 keyboard is only usable by seat 1. But the USB keyboard sends its input to both seats and I don't know why. 

Attached you will find my xorg.conf, a udev rule that creates the necessary links in /dev/input/ and a log file. Like I said before: these files are working without any problems on Hardy! 

(Yes: the udev rule creates two links for the USB keyboard. That's because the keyboard presents itself as two keyboards: the alphanumerical part and the extra multimedia keys. In order to use these special keys both parts of the keyboard have to be defined using a section "Input Device" for each part.)

What puzzles me a lot it the fact that xorg attaches the USB keyboard to seat 1 in spite the fact that I used 
```
Option      "AutoAddDevices"        "false"
```You can see this at the buttom of the log file:

```
(II) XINPUT: Adding extended input device "simple_kbd_seat_1" (type: KEYBOARD)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device HID 1267:0103
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device HID 1267:0103
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device HID 0461:4d03
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) UnloadModule: "kbd"
(II) mouse_seat_1: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "mouse"
(II) UnloadModule: "kbd"
 ddxSigGiveUp: Closing log
```"1267:0103" is the USB keyboard. Strange. But, at the same time, the mice work independently.

So, has anyone got a multiseat machine running in Jaunty? If so: what options do you use to separate the input devices? Are there any options I haven't found yet?

Many thanks in advance for any help.

---

### Post by knight187 on 2009-09-07
I have been running multiseat in jaunty (ubuntu, not kubuntu) for a few months now and it works really well. I have created a howto using my experience, here is the link. I'm not sure how different it will be in kubuntu but the xorg.conf should be the same for both.

[http://www.brucerenner.org/ubuntu-and-multiseat-howto](http://www.brucerenner.org/ubuntu-and-multiseat-howto)

Good luck, Cheers.

---

### Post by Wolfgang.Klein on 2009-09-08
Thanks for the hint. 

Actually I decided to stay with Hardy as long as possible, because after a few sessions I came to the conclusion that I don't quite like KDE4. There are too many things that don't work at all or that don't work well enough for me. 

If I could have KDE3 on Jaunty I wouldn't hesitate to install it again, because it starts much faster than Hardy on my machine. But I guess that will stay a dream.

---

