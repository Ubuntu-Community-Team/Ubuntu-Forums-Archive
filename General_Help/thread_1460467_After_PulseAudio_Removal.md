---
title: "After PulseAudio Removal"
date: 2010-04-22
forum: General Help
---

### Post by David Vincent-Jones on 2010-04-22
Ubuntu 9.10

In order to resolve problems with sound on Skype I have removed PulseAudio. This has been a total success .. however by doing this I have lost my desktop Sound Volume Control which is a bit of a nuisance.

AlsaMixer apparently has no desktop Volume Control. 

Is there a way to replace the volume icon?

---

### Post by themusicalduck on 2010-04-22
You might be able to use gnome-volume-control-applet instead.

Open a terminal (Applications > Accessories > Terminal) and type it in ```
gnome-volume-control-applet
```
If it works then you could set it to run on startup at System > Preferences > Startup Applications. Click on Add and put gnome-volume-control-applet in the Command box.

---

### Post by David Vincent-Jones on 2010-04-22
In terminal "gnome-volume-control-applet" indicates that the applet is already running.

System>Prefferances > Preferred Applications ... indicates that the button should already be showing on the desktop --- but it isn't

The 'Add-to-Panel' option on the task bar appears not to accept "gnome-volume-control-applet" as being valid.

Somehow when PulseAudio was zapped the volume control went with it.

---

