---
title: "Mute keyboard shortcut not working"
date: 2009-09-03
forum: General Help
---

### Post by Mr_Lazy on 2009-09-03
Hi,

I am on hardy Heron, and I thought I would set a mute key in keyboard shortcuts. So I chose Ctrl+Shift+M. But when I use this shortcut, a large transparent mute icon is displayed in the main screen, nothing happens to the volume control icon in the panel and I still have sound.

I can go into the volume control and mute as normal, but it would be nice to assign a keyboard shortcut to this.

Any ideas what is going on here and how to fix it?

Thanks,
L

---

### Post by P4man on 2009-09-03
your gnome mixer and the general sound mixer may be set differently.

Go to system > preferences > sound and make sure everything is set to alsa or pulseaudio (which ever you are using) and check the default mixer track. It should use the same device (alsa or pulse playback) and the master channel should be selected.

Then right click the gnome volume icon in the system tray, select preferences, and make sure its set to the same as well.

---

### Post by Mr_Lazy on 2009-09-03
Wow thanks, there was a decrepency in system > preferences > sound, made them all the same (alsa) and now it works perfectly. 

Thanks for the quick response!

L

---

