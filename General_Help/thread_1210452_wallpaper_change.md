---
title: "wallpaper change"
date: 2009-07-11
forum: General Help
---

### Post by mCion on 2009-07-11
in ubuntu 9.04 when you change the wallpaper it does so by a gradual fading.  Is there a way to turn this off?

I ask this because I had in the previous ubuntu edition a script for changing wallpapers depending the time of day.  With this "new" and "incorporated" feature in 9.04, when i'm playing music it chops up when changing wallpapers, and it is not as smooth as before.

any help would be appreciated

---

### Post by Jebtrix on 2009-07-11
Yes there is a way thankfully. 

```
gksudo gedit
```

in a new text file write:

```
gtk-enable-animations = 0
```

Save as gtkrc in /etc/gtk-2.0/

Then logout and back in.

---

### Post by mCion on 2009-07-11
Thank you!!!

---

