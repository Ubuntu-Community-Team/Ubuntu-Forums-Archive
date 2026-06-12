---
title: "Dual Point TouchPad driver resynced"
date: 2006-05-03
forum: General Help
---

### Post by thebasard on 2006-05-03
I'm having an issue with a Dell Latitude D600 where occasionally the mouse driver (apparently) has problems and the result is that I'm no longer able to left-click or right-click on anything, though the mouse moves freely across the screen.  I'm usually able to pull out of this by switching to the console via ctl+alt+f4 and back to Gnome again with ctl+alt+f7.

I see the following in dmesg:
[4947465.280000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 lost sync at byte 1
[4947465.283000] psmouse.c: DualPoint TouchPad at isa0060/serio1/input0 - driver resynched.

Any help would be great!

---

### Post by sypher7 on 2007-03-08
I'm also having the same problem. Also a Dell Latitude D600, but using Gentoo. 

I can sometimes switch around in virtual desktops or click around and sometimes I can regain functionality; however, the ability to emulate the middle mouse (click left and right at the same time) is totally lost unless I suspend and come back or reboot altogether.

I'm getting the same error message reported above.

In case it wasn't obvious, this laptop has both a normal touchpad and a pointer device embedded in the keyboard, each with their own mouse buttons.

I haven't found any good solutions for this yet, but if I do, I'll post it here.

---

