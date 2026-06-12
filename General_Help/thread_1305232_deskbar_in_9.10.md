---
title: "deskbar in 9.10"
date: 2009-10-29
forum: General Help
---

### Post by tk03759 on 2009-10-29
What happened to deskbar in 9.10??? It's not available to add to the panel.

I tried "sudo apt-get install deskbar-applet" but when it was done, I still couldn't add it.

Deskbar is my favorite.

---

### Post by tk03759 on 2009-10-30
I'm really surprised deskbar isn't installed by default.

I figured it out btw for any confused users in the future: after the install of deskbar-applet, gnome-panel needs to be restarted before you can actually add deskbar.

Either do

```
killall gnome-panel
gnome-panel
```-OR-

 Log out and log back in before trying to add deskbar to your panel.

Silly me . :oops:

---

### Post by LBAWinOwns on 2009-12-05
Works great in no-time.

Thank you very much. :)

---

