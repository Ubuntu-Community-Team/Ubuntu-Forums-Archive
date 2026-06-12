---
title: "kernel issue usb type."
date: 2011-03-09
forum: General Help
---

### Post by ulao on 2011-03-09
I have no idea where to ask this, but I was hopping there was a way to fix this without rebuilding the kernel ( long shot Im sure )

This is a normal usage list for USB HID.
Generic Desktop
0x00 Undefined
0x01 Pointer
0x02 Mouse
0x03 Reserved
0x04 Joystick
0x05 Game Pad
0x06 Keyboard
0x07 Keypad
0x08 Multi-axis Controller

Ubuntu for what ever reason see **0x05 Game Pad** as a mouse? The 05 hex is for a gamepad the difference in that from joystick is support for FFB ( rumble ). If you plug in a game pad deceive ( 0x05), it shows up as a mouse.

---

