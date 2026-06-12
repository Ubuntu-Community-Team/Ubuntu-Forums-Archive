---
title: "Rhythmbox's new status icon is UGLY in ubuntu maverick"
date: 2010-10-12
forum: General Help
---

### Post by okmat on 2010-10-12
Can someone please tell me how to change it? it doesn't change when I change the icon set

---

### Post by okmat on 2010-10-12
nevermind, I found a solution, sudo nautilus, then go to /usr/share/icons/hicolor/22x22/apps and replace rhythmbox.png with the icon you want. You'll have to repeat this for the 22x22, 24x24, 32x32, 48x48 etc folders

For radiance I used a .svg icon located at /usr/share/icons/ubuntu-mono-light/apps/24/rhythmbox-panel.svg opened with GIMP, scaled to the proper size and saved as .png

It takes a few rhythmbox/session restarts to appear though.

Shouldn't all standard apps follow the tango guidelines for the notification area icons?

---

### Post by lores on 2010-10-14
Thanks for the info. I substituted the relevant icons, but still no results in the tray. The icon in the gnome-menu changed after re-login. I'm using Radiance. Any ideas?

PS
I also logged in graphically as root, as I had not used rhythmbox this way, hoping that there would be no cache. However, the icon appeared ugly as usual...

EDIT
File permissions and icon parameters seem to be the same as originally.

EDIT II
There seems to be a much less intrusive way of changing icons on a per-user basis - ~/.icons. E.g. for mono-light, I had to place rhythmbox.svn (png or constant-pixel folders (e.g. 24x24) will also do) in ```
/home/lores/.icons/ubuntu-mono-light/scalable/apps
``` and restart Rhythmbox once.

---

