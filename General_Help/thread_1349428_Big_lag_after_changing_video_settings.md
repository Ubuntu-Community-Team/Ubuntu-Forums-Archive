---
title: "Big lag after changing video settings"
date: 2009-12-08
forum: General Help
---

### Post by Toreddo on 2009-12-08
Hello everyone,

I've installed Ubuntu eee (or EasyPeasy) on my eee pc. It has been running very well untill now. I connected a second display, but it wouldn't recognize it, so i played with the video settings and it worked. But now without a display connected it's very very laggy. It looks like the resolution is not native anymore. Is that possible? I have tried changing my settings again but it wouldn't work.. :(

I hope someone knows how i can reset this.

Thanks,

Chris

---

### Post by Toreddo on 2009-12-08
If i view /etc/X11/xorg.conf i can see the following lines:
SubSection "Display"
         Virtual 2160 768
EndSubSection

is this standard?

---

### Post by Toreddo on 2009-12-08
Ok i fixed the problem,
just went trough those steps and rebooted:
nano /etc/X11/xorg.conf

---

