---
title: "Screen locking in Ubuntu 11.10"
date: 2011-10-02
forum: General Help
---

### Post by Lodmot on 2011-10-02
Hi.
I'm having a serious problem with my custom built desktop computer in Ubuntu 11.10. Literally 1 second after I take my hands off of the mouse or keyboard, the screen fades to black. It only happens on my desktop, not my laptop, and they're both running the same exact version of Ubuntu with all the latest updates. 

I have a feeling it has to do with my desktop computer being hooked into an HDTV. I believe my desktop's graphics card is an ATI Radeon HD 4350, and it's hooked to the TV through the HDMI port. 

I apologize if this is in the wrong forum, but watching the screen turn black so much is actually making me nauseous..

---

### Post by Linuxratty on 2011-10-02
Go to screen saver and un-click lock screen when screen saver is active.

---

### Post by Lodmot on 2011-10-02
> **Linuxratty said:**
> Go to screen saver and un-click lock screen when screen saver is active.
Tried it, didn't work. :P
And this is 11.10, so there aren't any screensavers in this build of Ubuntu that I'm running...
But there is an on/off switch for lock screen, and I tried that.

---

### Post by grahammechanical on 2011-10-02
Have you considered the menu on the HDTV? That will have energy saving options. My HDTV does. I have set my options to OFF. I am not using HDMI but the earlier DVI.

Regards.

---

### Post by Lodmot on 2011-10-02
> **grahammechanical said:**
> Have you considered the menu on the HDTV? That will have energy saving options. My HDTV does. I have set my options to OFF. I am not using HDMI but the earlier DVI.

Regards.
I tried that, but it didn't seem to work. 
Does anyone else have any problems with TV's hooked into their computers?

---

### Post by Lodmot on 2011-10-02
Well, I couldn't fix the underlying problem, but I did find a workaround. 
By uninstalling the gnome-screensaver package and installing xscreensaver, the problem immediately ceased. So, I guess I must've stumbled into some sort of crazy glitch with gnome-screensaver. At least now it's not fading to black anymore, and I've got over 200 screensavers now..... Way to go above and beyond. xD

---

### Post by sirnicolas21 on 2011-10-06
came across the same problem.... this should fix it really fast... just save whats needs to be saved before restarting lightdm
```

sudo apt-get install gnome-screensaver-
sudo lightdm restart

```

---

