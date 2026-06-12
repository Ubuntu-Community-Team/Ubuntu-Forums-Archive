---
title: "How to block a usb device with udev?"
date: 2011-10-31
forum: General Help
---

### Post by Jumphog on 2011-10-31
(Running Lucid 10.4 LTS)

Ive just found out that my microsoft wireless mouse's usb receiver is actually a composite device that shows up as a mouse, keyboard and joystick. This wouldnt be a problem but the joystick is detected as having 40 buttons and 37 axes all of which are at extreme positions. The upshot is that a couple of games I have are getting confused by this device and I need to stop the joystick from getting detected.

After searching around for a couple of hours I thought Id found the answer - make a udev rule with the "ignore_device" option. Unfortunately it seems that this option doesnt exist any more, so how can I make udev do nothing when this usb receiver is detected?

---

