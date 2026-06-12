---
title: "Touchpad not working"
date: 2010-11-10
forum: General Help
---

### Post by cd-r80 on 2010-11-10
Touchpad has stopped working after some update. How to re-enable it? I don't have usb mouse. No PS2 port. pci=noacpi does not help. apt-get install xserver-xorg-input-synaptics does not help, already installed.

---

### Post by gyussz on 2010-11-10
> **cd-r80 said:**
> Touchpad has stopped working after some update. How to re-enable it? I don't have usb mouse. No PS2 port. pci=noacpi does not help. apt-get install xserver-xorg-input-synaptics does not help, already installed.

If your system disabled it for any reason, try this in terminal:
```
gconftool -s -t bool /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```

---

### Post by flipper T on 2010-11-10
tried fn + f1 ?

---

### Post by cd-r80 on 2010-11-10
fn+F1 Does not help. Neither other command. I use Xubuntu so that command line was strange for me /desktop/gnome/...?

---

