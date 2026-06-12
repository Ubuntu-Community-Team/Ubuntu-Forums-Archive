---
title: "Help with USB Joystick"
date: 2006-03-15
forum: General Help
---

### Post by dcviana on 2006-03-15
I've recently instaled Ubuntu Breezy and tried installing my TwinShock USB Gamepad. I instaled the "joystick" package and "jcalibration" and all went well

I ran jcalibration and was amazed, it detected my gamepad perfectly (it event detected its name, TwinShock) and I calibrated it succesfully.

But then I tried using it and noticed that the axis don't work at all, only the buttons. I tried ZSnes, XMame, Snex9x and other games I downloaded via synaptic, and all of them showed this problem.

Can someone help me? The axis work in jcalibration, why they don't work in games?

Thanks.

---

### Post by dcviana on 2006-03-19
I just noticed that some other posts reported this same problem with USB gamepads, and it seems the workaround is to run games with root permission using sudo. It worked for me but I need a better solution, has anyone found it?

Thanks

---

### Post by mariusthart on 2007-08-18
Do not use jscalibrator. Use jscal instead, it is a command-line tool you can get by installed joystick. You can use it with a command like: jscal /dev/input/js0

---

### Post by elmagnifico on 2007-09-15
i think i have the same problem here but i've tried remapping the pad to keyboard using joy2key and it returned with this msg :
[COLOR="Sienna"]Error opening /dev/js0!
Are you sure you have joystick support in your kernel?[/COLOR]

and still have the buttons only without any axis working.
any suggestions ?

---

### Post by 1veedo on 2007-10-13
sudo ln -s /dev/input/js0 /dev/js0


Btw I can calibrate my joystick and everything but I cant get any games to recognize it.

---

### Post by eldanialonso on 2008-06-06
> **mariusthart said:**
> Do not use jscalibrator. Use jscal instead, it is a command-line tool you can get by installed joystick. You can use it with a command like: jscal /dev/input/js0

Thanks a lot! After doing this, I was able to get it working :)

---

