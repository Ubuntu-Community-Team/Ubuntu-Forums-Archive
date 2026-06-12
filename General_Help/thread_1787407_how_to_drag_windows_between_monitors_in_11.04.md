---
title: "how to drag windows between monitors in 11.04"
date: 2011-06-21
forum: General Help
---

### Post by ububeginner on 2011-06-21
Hi there,
I just installed 11.04 and I'm trying to set up dual monitors. I've installed the nvidia drivers and set the monitors to separate xscreen mode. It works fine, the mouse cursor moves freely between monitors, but when I try to drag windows over, it just wants to resize them to half screen. 
I've tried disabling grid in ccsm, and it stops the resizing thing, but I still can't drag the windows across.

Any ideas on how to accomplish this?

---

### Post by ububeginner on 2011-06-21
Is it ok to bump?

---

### Post by Tuliku on 2011-06-21
I have the same issue, did a fresh install, but no matter which option i use, i cant get the extended screen to work..

---

### Post by ububeginner on 2011-06-23
Is there a keyboard shortcut or a way to create one?

---

### Post by life in color on 2011-06-23
are you able to create files and folders in the second screen at all? I don't have the slightest clue how to make this work but I will try to help if I can.

---

### Post by ububeginner on 2011-06-23
> are you able to create files and folders in the second screen at all?I left clicked on the desktop on the second monitor and created a folder. When I opened the folder it opened half out of the screen to the right, the primary monitor is on the left.
The window has no top bar and I can't access the menus from the unity bar (the unity bar does not extend to the second monitor), and now I have no way to close it, move it, or do anything with it as most of it is outside of the screen.
I cant switch to the window with alt+tab either.

---

### Post by ububeginner on 2011-06-23
Problem solved

nvidia x server settings
configuration: twin view
set the monitor you want the unity launcher on as primary display
log out and then back in

---

### Post by Tuliku on 2011-06-26
Yep, worked for me too, thanks

---

