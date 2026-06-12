---
title: "Disabling pointing devices"
date: 2009-11-05
forum: General Help
---

### Post by mch0lic on 2009-11-05
I have really annoying and I mean really really annoying problem with self moving mouse pointer. I'm not sure what causes this behavior but it should be touch-pad or the joystick mounted in keyboard.

The question is how I can disable these pointing devices and use only external usb mouse. I tried to check xorg.conf but it's not present or I'm looking in the wrong place (/etc/X11/)


OS: Ubuntu 9.10

---

### Post by VolkerLanz on 2009-11-06
> **mch0lic said:**
> I have really annoying and I mean really really annoying problem with self moving mouse pointer. I'm not sure what causes this behavior but it should be touch-pad or the joystick mounted in keyboard.

The question is how I can disable these pointing devices and use only external usb mouse. I tried to check xorg.conf but it's not present or I'm looking in the wrong place (/etc/X11/)

OS: Ubuntu 9.10

You might try uninstalling xserver-xorg-input-synaptics, but this is really just a guess. I don't know if this breaks anything, in other words. Or if Ubuntu will even let you uninstall it without too much complaining.

Xorg in Ubuntu 9.10 doesn't need a config file anymore, that's why you don't find one in /etc/X11. If you create one, it will still use it, however.

---

### Post by mch0lic on 2009-11-07
If unbuntu do not use xorg.conf so I guess it should be another config where all devices or at least input are described?

---

