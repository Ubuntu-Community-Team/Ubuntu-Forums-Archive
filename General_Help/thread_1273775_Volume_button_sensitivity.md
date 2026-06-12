---
title: "Volume button sensitivity"
date: 2009-09-23
forum: General Help
---

### Post by cos85 on 2009-09-23
The volume up/down buttons on my laptop are too sensitive. That is, they change the volume by +-7%. I want to make that step value smaller, e.g. 2 or 3%.

Can't find anything on the net, and not sure if I'm really searching for the right things. Any ideas?

---

### Post by tkoco on 2009-09-23
Sounds like the laptop is treating the volume u/d buttons like the Pageup/Pagedown keys. ```
man alsamixer
```for more information on the mixer volume adjustment.

> **cos85 said:**
> The volume up/down buttons on my laptop are too sensitive. That is, they change the volume by +-7%. I want to make that step value smaller, e.g. 2 or 3%.

Can't find anything on the net, and not sure if I'm really searching for the right things. Any ideas?

---

### Post by cos85 on 2009-09-24
I've had a read of the man page, but I can't see any way to change it. I would guess this is tucked away in a config file somewhere -- hopefully it's not hardcoded.

---

### Post by cos85 on 2009-09-24
shameless bump

---

### Post by cos85 on 2009-09-24
Ok, I'm sure there must be others who want to know the answer to this, so here's what I've got:

* Go into Preferences > Keyboard shortcuts and clear (using backspace) the volume up/down shortcuts
* Install compizconfig-settings-manager
* Open compizconfig, enable the "commands" option and enable two key bindings. Bind one to volume up and one to volume down in the Key bindings tab. In the command tab add these two commands

amixer sset Master,0 X%-
amixer sset Master,0 X%+

replacing the Xs with the amount to change the volume. 

Note that this won't show the notification bubble thing, but I guess that's not so bad.

---

### Post by nrgetik on 2009-10-11
G'day all, First time poster/commenter here. I've just recently upgraded to the Karmic beta, primarily so i could use a USB audio device that would have otherwise required me to recompile the kernel in Jaunty. Anyway, getting to the point, i discovered a MUCH easier means of changing the sensitivity of the volume control than what's listed about AND it means you don't have to lose your volume notification popup....
 
Press Alt + F2 and type in "gconf-editor" (without "" obviously)
 
Navigate to "Apps" then to "gnome_settings_daemon" and change the "volume_step" value to whatever you desire (i think the default was 6 on mine).
 
Piece of cake! :guitar:

---

### Post by Rogerborg on 2010-01-26
=D> Winner!  Thanks, that's exactly what I was looking for.  6 is way too coarse for a default granularity.

---

### Post by saygin on 2010-01-31
is there a KUBUNTU way of doing the same thing?

---

### Post by satrapes on 2011-10-03
Excellent thank you very much.

---

### Post by kid1000002000 on 2011-10-16
doesnt work in 11.10. subscribe to this bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/871133)

---

