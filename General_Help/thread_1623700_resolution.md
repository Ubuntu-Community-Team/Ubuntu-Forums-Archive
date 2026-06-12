---
title: "resolution"
date: 2010-11-16
forum: General Help
---

### Post by wombil on 2010-11-16
Hey Guys,big trouble here I think.My desktop screen was a bit large for my monitor screen so I was mucking around with the resolution.I set it very low
600 or something to try and now when I try to start up I get as far as name and password,then the brown screen comes on for a few seconds and goes black with an i in a green square and the message,"Mode not supported".
I have pressed esc and tried the repair options but to no effect.
Have tried to load in safe mode but the same thing happens.
 I have got to a stage where the desktop is black with my icons displayed and a lot of error messages but no task or tool bar,"probably hidden off the screen",so I cannot get to the system heading to adjust the resolution back.On the options at startup I have got a terminal box but I have no idea what I could type in it.
 My system is Ubuntu 8.04.1 .
Any help with this is greatly appreciated.
wombil.

---

### Post by wombil on 2010-11-17
Hi Guys,getting desperate here,
If I install 10.04 over 8.04 can I transfer all my data to the new install at the same time?

---

### Post by devildoc5 on 2010-11-17
try booting it from GRUB into a shell (CTRL+ALT+f1)

then try typing in "xrandr" and see if that helps out with the resolution problems.

The other option would be to boot into "safe mode" and try and debug it from there, I BELIEVE it has a Video setting you can change...

---

### Post by Vigh on 2010-11-17
hey mate, reset the computer, before it boots up the ubuntu logo- hold down ctrl-F2 as its booting- select recovery mode kernel- run fail safe X- reconfigure graphics- restore defaults, reboot

should restore the monitor to a usable resolution

re-install your graphics drivers

you have a working system again

---

### Post by wombil on 2010-11-17
Thanks fellers,I have tried in the safe mode from "options" at startup but still got the "Mode not supported" message. I have got some keyboard commands and may be able to unmaximise the window and get to the top of the page and access the system menu.Can't get back to it for a while but will let you know how I go with it.
Thanks again.

---

### Post by wombil on 2010-11-29
Hey guys,been away for a while,long time getting back.
A nephew called in yesterday and after fiddling for 20 minutes or so,
1, opened options,{bottom left hand corner before entering name,password}.
2, opened failsafe mode and terminal
3, entered,"gnome-panel," which revealed the toolbar/taskbar.
4, altered the resolution to 1024x768.
5, restarted and all is back to normal.
 Thanks for all the suggestions,hope this helps someone else.

---

