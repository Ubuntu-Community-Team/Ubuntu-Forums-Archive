---
title: "Keyboard input ceasing to work, but HAL seems to be fine"
date: 2011-10-17
forum: General Help
---

### Post by tocia on 2011-10-17
Hi,
my keyboard and mouse freeze as soon as X start.
At the login screen nothing work, unless I switch to raw keyboard with alt-SysRq-r, and then I can open a terminal, where keyboard works with us layout (I'm using ch french layout). As reported at the end of this link [https://wiki.ubuntu.com/X/Troubleshooting/HalBreaksKeyboardAndMouse](https://wiki.ubuntu.com/X/Troubleshooting/HalBreaksKeyboardAndMouse)  it may be a keyboard layout specific issue, in fact I remember deleting the us layout a couple of hours before it happens. 
Any suggestion on resolving the issue are welcome. Thx.


Update

I edited the xorg.conf with "AllowEmptyDevices" "False" and nothing seems to happen.

---

### Post by tocia on 2011-10-18
With "AutoAddDevices" "False" instead the mouse starts working again  and I've been able to log in with the On Screen Keyboard, but so far I  'm still not able to bring back the keyboard in the GUI. The Xorg.0.log  shows right after the line (**) Not automatically adding devices   another line with (==) Automatically adding devices, could this be an  issue?

If needed I can post the whole log files, just ask.

---

