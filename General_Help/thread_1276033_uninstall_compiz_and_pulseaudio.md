---
title: "uninstall compiz and pulseaudio"
date: 2009-09-26
forum: General Help
---

### Post by xnsine on 2009-09-26
Hi, so, I would like to uninstall compiz and pulseaudio, since I dont use either, and they are just annoying and full of errors, specially pulseaudio.  Im more interested in uninstalling pulseaudio actually, compiz I have it deactivated now.  So, if I uninstall all the pulseaudio packages, will that break the system?  I would need to enable either oss or alsa afterwards too, right?

thank you

---

### Post by Psy[H[] on 2009-10-03
If you are using 9.04, then you may kill pulseaudio, set all output to alsa, uninstall pulseaudio package and remove pulseaudio from session startup.
Sound will work perfectly.

But in 9.10 there are big problems: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/440465)

---

