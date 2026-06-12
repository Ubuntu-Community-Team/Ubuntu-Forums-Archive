---
title: "Using Ubuntu with no mouse or keyboard"
date: 2010-01-07
forum: General Help
---

### Post by glennwalsh on 2010-01-07
Hi everyone

I know that by pressing CTRL+SHIFT+NUMLOCK I can use the number pad as a pseudo mouse, but is it possible to force this condition at boot without needing to enter a key press?

(I'm putting a computer in my car running Ubuntu and have decided to do away with both the mouse and keyboard and control it from a joystick on the steering column.  This has been wired to the circuit out of an old keyboard to mimic the arrow keys on the numeric keypad.)

All the best

Glenn
(Belfast)

---

### Post by slakkie on 2010-01-07
I think it is, but I'm not sure.

You have a monitor on the PC? 
Perhaps use the joystick as a mouse and install a virtual keyboard:

matchbox-keyboard
xvkbd
kvkbd

I sometimes use kvkbd, works really well, looks a bit like the keyboard on an iphone/android. Basicly it is the same, a virtual keyboard ;)

And you might want to install an openssh-server on the computer, so you can administrate it remotely. Think that will come in handy if you encounter some issues which requires a lot of keyboard/mouse action.

---

### Post by glennwalsh on 2010-01-07
Thanks for the tip, that might work, although the 'joystick' is wired as a keypad rather than a games joystick.
 
I'll try it and see what happens.
 
Thanks again
 
Glenn

---

