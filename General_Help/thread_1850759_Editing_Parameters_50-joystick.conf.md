---
title: "Editing Parameters 50-joystick.conf"
date: 2011-09-27
forum: General Help
---

### Post by Stoppelmonster on 2011-09-27
I am using a Macally iShock II, I need help editing parameters in 50-joystick.conf to edit button functions on the gamepad itself. 

currently, 50-joystick.conf looks like:

[B]Section "InputClass"
Identifier "joystick catchall"
MatchIsJoystick "on"
MatchDevicePath "/dev/bus/usb/004/001*"
Driver "joystick"
 Option "StartKeysEnabled" "False"
    Option "StartMouseEnabled" "False"

EndSection[/B]

---

