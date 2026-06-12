---
title: "Touchscreen jitter with evdev on PandaBoard"
date: 2012-09-04
forum: General Help
---

### Post by timow on 2012-09-04
I have a touchscreen controller "3M USB Touchscreen - EX II" with a capacitive touchscreen connected to a PandaBoard.

The touchscreen has a strong jitter.
When pressing and holding a finger on the touchscreen, the mouse pointer "jumps" around the finger.
The jumps are not far from the finger, but enough to be irritating.

Is there any way to eliminate this jitter for the touchscreen?

The PandaBoard has installed the OMAP4 variant of Ubuntu 10.04.
Xorg automatically detects the touchscreen and uses the "evdev" driver to control the touchscreen.
Calibration with "xinput_calibrator" works fine.

---

