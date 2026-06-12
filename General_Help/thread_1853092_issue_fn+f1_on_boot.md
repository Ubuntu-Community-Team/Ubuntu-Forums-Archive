---
title: "issue fn+f1 on boot"
date: 2011-10-01
forum: General Help
---

### Post by jonee316 on 2011-10-01
Hi!

I would want to "type" automatically this combination on boot (or on login). Can anyone help me to do it?

This has something to do with the multimedia leds on my laptop which I want to be turned off on boot. 

Thanks!

---

### Post by Toz on 2011-10-07
What make/model of computer do you have?

Open a terminal window and run:
```
xev | grep keycode
```
A window will popup on your screen. Press your Fn+F1 key combination, and hopefully something will display in the original terminal window related to a keycode value. e.g.:
> state 0x0, keycode 235 (keysym 0x1008ff59, XF86Display), same_screen YES,
Post back the results.

If you get a keycode returned, you can try to manually initiate the action via:
```
sudo acpi_fakekey <keycode>
```
This code can then be added to your startup scripts.

---

