---
title: "Unable to unlock from gnome-screensaver. 11.10 + Gnome 3."
date: 2011-12-02
forum: General Help
---

### Post by v3trae on 2011-12-02
Hey guys,

I'm having some problems regarding unlocking gnome-screensaver. it seems that about 30% of the time, when I come back and unlock the machine, the login dialogue window wont open. It will stay on the black page (date at the top) and never open any other prompt. Switching to console then back to X doesn't correct it. So far the only real fixes I've been able to find are to kill gnome-screensaver completely, restart lightdm, or restart the machine. Haven't found anyone else having this problem through my googling.

Note that the dialogue box is ALWAYS available directly after locking. (Like I can lock, then move the mouse/hit a key and the password dialogue will come up). But if I leave for a few minutes and come back it will not.

Truthfully, I'm not sure where to start. 

Appreciate any and all assistance. If you need any specific information from me, ask and I'll do my best to get it for you.

Thank you for your time.

---

### Post by v3trae on 2011-12-07
> **v3trae said:**
> Hey guys,

I'm having some problems regarding unlocking gnome-screensaver. it seems that about 30% of the time, when I come back and unlock the machine, the login dialogue window wont open. It will stay on the black page (date at the top) and never open any other prompt. Switching to console then back to X doesn't correct it. So far the only real fixes I've been able to find are to kill gnome-screensaver completely, restart lightdm, or restart the machine. Haven't found anyone else having this problem through my googling.

Note that the dialogue box is ALWAYS available directly after locking. (Like I can lock, then move the mouse/hit a key and the password dialogue will come up). But if I leave for a few minutes and come back it will not.

Truthfully, I'm not sure where to start. 

Appreciate any and all assistance. If you need any specific information from me, ask and I'll do my best to get it for you.

Thank you for your time.


Update: 
Although it does not DISPLAY the login prompt, the prompt is there, and typing in your password does log you in. This isn't preferred, but at least it's working.

---

### Post by thaelim on 2011-12-07
This is a known bug with Gnome 3 and the nVidia binary drivers. The workaround, as you found, is to simple go on like the dialog is there and you'll be able to unlock. You could also disable screen locking in System Settings. 

I believe for future versions they are planning to remove gnome-screensaver altogether and integrate the screen locking into the display manager. Hence why no effort is being put into fixing gnome-screensaver...

---

