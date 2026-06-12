---
title: "Keyboard not working in X, just the right-side numpad+numlock"
date: 2010-11-30
forum: General Help
---

### Post by herbster on 2010-11-30
Quite a strange problem, I am an Arch user but no help so far from the forum there and just giving it a shot here. Logging in/out of X after a recent upgrade and now I can't type anything with the main part of my keyboard, only the numpad on the right side works (numbers with numlock, cursor moves directionally without, etc.). Here's relevant section of /etc/X11/xorg.conf.d/10-evdev.conf:
```
Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"

        # Keyboard layouts
        Option "XkbLayout" "ca"
        Option "XkbOptions" "grp:alt_shift_toggle, grp_led:scroll, terminate:ctrl_alt_bksp"
EndSection
```

Here's some tail from the xorg.log:

```
[   891.177] (II) config/udev: Adding input device LITEON Technology USB Multimedia Keyboard (/dev/input/event1)
[   891.177] (**) LITEON Technology USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[   891.177] (**) LITEON Technology USB Multimedia Keyboard: Applying InputClass "Keyboard Defaults"
[   891.177] (**) LITEON Technology USB Multimedia Keyboard: always reports core events
[   891.177] (**) LITEON Technology USB Multimedia Keyboard: Device: "/dev/input/event1"
[   891.199] (--) LITEON Technology USB Multimedia Keyboard: Found keys
[   891.199] (II) LITEON Technology USB Multimedia Keyboard: Configuring as keyboard
[   891.199] (II) XINPUT: Adding extended input device "LITEON Technology USB Multimedia Keyboard" (type: KEYBOARD)
[   891.200] (**) Option "xkb_rules" "evdev"
[   891.200] (**) Option "xkb_model" "evdev"
[   891.200] (**) Option "xkb_layout" "dvorak"
[   891.200] (**) Option "xkb_variant" ", phonetic"
[   891.200] (**) Option "xkb_options" "grp:alt_shift_toggle, grp_led:scroll, terminate:ctrl_alt_bksp"
[   891.201] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event2)
[   891.201] (**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
[   891.201] (**) Logitech USB-PS/2 Optical Mouse: always reports core events
[   891.201] (**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event2"
[   891.226] (--) Logitech USB-PS/2 Optical Mouse: Found 12 mouse buttons
[   891.226] (--) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
[   891.226] (--) Logitech USB-PS/2 Optical Mouse: Found relative axes
[   891.226] (--) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[   891.226] (II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[   891.226] (**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[   891.226] (**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   891.226] (II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[   891.226] (**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[   891.226] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration profile 0
[   891.226] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration factor: 2.000
[   891.226] (**) Logitech USB-PS/2 Optical Mouse: (accel) acceleration threshold: 4
[   891.226] (II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
[   891.227] (II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse0)
[   891.227] (II) No input driver/identifier specified (ignoring)
[   891.232] (II) config/udev: Adding input device PC Speaker (/dev/input/event5)
[   891.232] (II) No input driver/identifier specified (ignoring)
[   891.236] (II) config/udev: Adding input device Media Center Ed. eHome Infrared Remote Transceiver (1784:0001) (/dev/input/event6)
[   891.236] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): Applying InputClass "evdev keyboard catchall"
[   891.236] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): Applying InputClass "Keyboard Defaults"
[   891.236] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): always reports core events
[   891.236] (**) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): Device: "/dev/input/event6"
[   891.253] (--) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): Found keys
[   891.253] (II) Media Center Ed. eHome Infrared Remote Transceiver (1784:0001): Configuring as keyboard
[   891.253] (II) XINPUT: Adding extended input device "Media Center Ed. eHome Infrared Remote Transceiver (1784:0001)" (type: KEYBOARD)
[   891.253] (**) Option "xkb_rules" "evdev"
[   891.253] (**) Option "xkb_model" "evdev"
[   891.253] (**) Option "xkb_layout" "dvorak"
[   891.253] (**) Option "xkb_variant" ", phonetic"
[   891.253] (**) Option "xkb_options" "grp:alt_shift_toggle, grp_led:scroll, terminate:ctrl_alt_bksp"
```
I have tried disabling input hot-plugging and explicitly adding the keyboard, reinstalled xorg, I can't figure this out. Everything in X works fine, too, I just can't get the keyboard to work at all but for the numpad :(

Oh and have kernel 2.6.35.8 and Xorg-server 1.9.2

---

