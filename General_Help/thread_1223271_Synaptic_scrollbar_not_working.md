---
title: "Synaptic scrollbar not working"
date: 2009-07-26
forum: General Help
---

### Post by SKeaLoT on 2009-07-26
I have a Dell 1420n, which comes with a synaptics touchpad.
The touchpad works great, but for some reason the scrollbar capabilities of the touchpad are disabled, i also noted that in the **System > Preferences > Mouse** dialog, there is NO "Touchpad" tab.

I tried loading the evdev module (someone suggested it at these forums), but didn't work.

Any help will be greatly appreciated, as this is starting to get **REALLY** annoying

Edit: I'm running Jaunty

thx

---

### Post by darolu on 2009-07-26
[http://packages.ubuntu.com/jaunty/xserver-xorg-input-synaptics](http://packages.ubuntu.com/jaunty/xserver-xorg-input-synaptics)

[http://wiki.debian.org/XStrikeForce/InputHotplugGuide](http://wiki.debian.org/XStrikeForce/InputHotplugGuide)

---

### Post by SKeaLoT on 2009-07-26
I have that package installed, and I'm not really sure what to do with the other page...
btw, "$ sudo modprobe synaptics" returned "FATAL: Module synaptics not found."

---

