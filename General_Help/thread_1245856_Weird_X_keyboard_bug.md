---
title: "Weird X keyboard bug"
date: 2009-08-21
forum: General Help
---

### Post by aldimond on 2009-08-21
I'm running Kubuntu 9.04 on x86-64.  Occasionally, after my computer has been up and working normally for a long time, the keyboard will stop producing X events.  Everything else works fine, just not the keyboard.  The NumLock and CapsLock keys don't cause the keyboard lights to change.  Even if I open up the virtual keyboard (kvkbd) and click letters they don't get to my programs.

I don't have the box in its failing state right now but when I did I ssh'd into it and ran some tests.  First, I catted the appropriate /dev/input/event* file, mashed the keyboard, and saw the expected gibberish.  Next I ran xev on :0 and couldn't see any keyboard events, even from the virtual keyboard.  Next, I checked /var/log/Xorg.0,log and didn't see anything out of the ordinary.  I can tail -f the log file, unplug and replug the keyboard, and see some cool log spew:

```
(EE) HID 0430:0005: Read error: No such device
(II) config/hal: removing device HID 0430:0005
(II) HID 0430:0005: Close
(II) UnloadModule: "evdev"
(II) config/hal: Adding input device HID 0430:0005
(**) HID 0430:0005: always reports core events
(**) HID 0430:0005: Device: "/dev/input/event5"
(II) HID 0430:0005: Found keys
(II) HID 0430:0005: Configuring as keyboard
(II) XINPUT: Adding extended input device "HID 0430:0005" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) HID 0430:0005: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) HID 0430:0005: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) HID 0430:0005: xkb_layout: "us"
(**) Option "xkb_variant" "dvorak-intl"
(**) HID 0430:0005: xkb_variant: "dvorak-intl"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) HID 0430:0005: xkb_options: "lv3:ralt_switch"

```

But the behavior is exactly the same after re-plugging.  I also re-plugged one of my mice accidentally and it continued to work.

What seems really suspicious is that even the virtual keyboard doesn't work.  It seems like the problem must be in X somewhere but I really don't know where to look next.  Does anyone have any ideas?

(Also, what is the deal on these forums with the minimum tag length of 3 characters?  "X" is a very legitimate tag for this post!)

---

