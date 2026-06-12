---
title: "Problems with sound after updates yesterday"
date: 2010-11-21
forum: General Help
---

### Post by dsfitzpat on 2010-11-21
Hi,
I've been having problems with my sound after applying yesterday's updates to gnome-settings-daemon and indicator-sound.
The next time I logged in there was no sound at all - this turned out to be because for some reason the output device had changed from Internal Analog to HDMI (I don't have HDMI audio hooked up).
I changed it back, and sounds play now, but the behaviour on logging in is strange - the first few seconds when the login sound should be playing are just a ticking noise, and then the last few seconds play, but at half the volume.
My guess is that something got corrupted in my gconf settings, since things work properly when I use the login I have set up for my girlfriend.  I want to try fixing this by deleting config files from a shell and then logging in again so that the system regenerates the default files - so my question is, which files can I safely delete?

---

