---
title: "can't log into kde"
date: 2012-02-04
forum: General Help
---

### Post by lefuuuu on 2012-02-04
Hi all, I hope someone can help me.

So I stopped and started plasma desktop and everything came up back to working but the wallpaper and I couldn't right click on the desktop. I logged out and back in hoping it would do the trick but it wouldn't let me log into kde. It gave me some warning message about it no longer being valid. I log into gnome classic instead but even then the wallpaper is just blue and I can't right click on the desktop.  I... have no idea how to fix this or what even went wrong.

Oh, and this is on kubuntu 11.10

---

### Post by aasdfasdfg on 2012-02-05
Navigate to a terminal and check for broken packages with ```
dpkg-reconfigure -a
```
Check your running processes with top (or I prefer htop) to see what the system is trying to do. Once, I recall my gnome-session properties getting changed and I accidentally had a K desktop running on top of a GNOME desktop *behind* it.

If you can access gnome-panel while running gnome-classic, are you able to change your background?

And lastly, please post version and theme information if you have a chance.

---

