---
title: "Missing Master Volume"
date: 2010-01-11
forum: General Help
---

### Post by warfacegod on 2010-01-11
Several days ago, I noticed that something was missing from my Notification area. I thought oh well whatever, everything works so I'll ignore it. Well everything does work, however, it dawned on me that it was the Volume icon that was missing. I tried Adding it to panel, it isn't in the list when it used to be. I looked in my Prefs and Admin. menus and Sounds is gone from there too. I looked in Sounds & Video, no dice. I tried editing menus to seeing it was there add to the menu, nope.

I still have sound and I know Master Volume is still working because I can raise and lower the sound with my keyboard short cut. The OSD even pops up when I do. Thanks in advance.

---

### Post by SlugSlug on 2010-01-11
you should be able to right click a panel and add to panel - then jig it about to get in the notify bit

---

### Post by Leppie on 2010-01-11
try re-installing the media package:
```
sudo apt-get purge gnome-media
sudo apt-get install gnome-media
```

---

### Post by warfacegod on 2010-01-11
> **SlugSlug said:**
> you should be able to right click a panel and add to panel - then jig it about to get in the notify bit

I had already tried that. Still didn't work. Thanks though.

---

### Post by warfacegod on 2010-01-11
> **Leppie said:**
> try re-installing the media package:
```
sudo apt-get purge gnome-media
sudo apt-get install gnome-media
```

The purge told that it wasn't found, so I installed it and Sounds is back in menu. The icon still isn't on my Notif. Area but I haven't rebooted yet so that Startup Master Vol. can kick in. Seems to have worked quite well though. I wonder how gnome-media got removed in the first place, I'm pretty sure this was right after an update.

---

