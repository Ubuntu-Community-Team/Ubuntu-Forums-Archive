---
title: "IR receiver works like keyboard, but does not create /dev/input/ entries &amp; symlinks"
date: 2010-12-02
forum: General Help
---

### Post by scotty64 on 2010-12-02
I am having problems getting the IR remote of my Hauppauge WinTV USB2 to work with lirc. The problem is that no links are created under /dev/input, so I cannot tell lirc where to listen.
However, the IR receiver seems to work as keypresses on the remote are interpreted as keyboard input in a terminal.
Dmesg shows the following output for the IR when I plug the device in:

input: i2c IR (i2c IR (EM2840 Hauppaug as /devices/virtual/input/input18
ir-kbd-i2c: i2c IR (i2c IR (EM2840 Hauppaug detected at i2c-3/3-0030/ir0 [em28xx #0]

In comparison a Hauppauge HVR 900 works fine as it creates the links under /dev/input/by-path and by-id:
input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.7/usb2/2-2/input/input17

---

