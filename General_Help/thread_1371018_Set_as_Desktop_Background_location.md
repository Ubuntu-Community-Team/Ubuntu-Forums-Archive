---
title: "Set as Desktop Background location?"
date: 2010-01-02
forum: General Help
---

### Post by PDA1 on 2010-01-02
What's the location for the Desktop Background images?

I set one as my desktop image by doing the "right click set as desktop...." but I have no idea where on my machine the image is located.

---

### Post by PhrankDaChickenGeek on 2010-01-02
If you did that from firefox, it should be in your home folder as "Firefox_Wallpaper" or something

The default GNOME backgrounds are in /usr/share/backgrounds

To find where your current background is stored, press "Alt+F2" and enter "gconf-editor" - Then browse to /desktop/background/picture_filename

---

