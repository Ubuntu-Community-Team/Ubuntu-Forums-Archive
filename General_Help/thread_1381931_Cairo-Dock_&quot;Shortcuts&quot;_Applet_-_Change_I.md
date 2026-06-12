---
title: "Cairo-Dock &quot;Shortcuts&quot; Applet - Change Icons?"
date: 2010-01-15
forum: General Help
---

### Post by david.bell on 2010-01-15
I am running Ubuntu Karmic and I have the Cairo-Dock as my launcher.  I am trying to figure out how to change the icons in the "Shortcuts" applet, but I am running into trouble.  I did find where the icons are stored, but I was looking for a way to point to different icons instead of overwriting the originals.  I have attached a screenshot of the applet and icons in question.

By the way, I did try changing the overall icon theme of Cairo-Dock and that seems to have absolutely 0 effect on the applet icons.

Dave

---

### Post by fabounet on 2010-01-15
applets have their own icons, not some icons from an icon theme.
the nautilus launcher has an icon named "nautilus", so changing the theme will change the icon, but applets have any kind of images.
you can just set the image you want for any applet.

as for Shortcuts, the names are provided by Gnome, but the dock offers a way to overload them in ~/.config/cairo-dock/current_theme/icons.
you just have to respect the names of the icons (something like gnome-volume.png)

some themes do that, like the theme "Tux and Tosh".

---

### Post by david.bell on 2010-01-19
I ended up having to do that.  I was hoping there was an applet setting that would allow me to change the icons without having to put them in that folder and rename them.  But, at least it works this way.

---

