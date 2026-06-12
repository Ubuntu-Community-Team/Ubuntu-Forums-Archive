---
title: "Change the Ubuntu icon to the default GNOME icon"
date: 2011-07-08
forum: General Help
---

### Post by Cgenet on 2011-07-08
I use Ubuntu 10.04 LTS.

How can I change the Ubuntu icon to the default GNOME icon, on the main GNOME menu, using an official or 'clean' way of doing it - no hax?

---

### Post by pqwoerituytrueiwoq on 2011-07-08
change theme

---

### Post by Cgenet on 2011-07-08
I am using the Clearlooks theme, but the Clearlooks theme has a foot, and this 'Clearlooks' them has the Ubuntu logo.

---

### Post by wojox on 2011-07-08
It's been a while. Look in Gconf-editor > apps > panel > objects > custom_icon. Click in it and set the path to your new icon. Look in /usr/share/pixmaps/ there are some good gnome icons in there.

Make sure to check use_custom_icon as well.

---

### Post by Cgenet on 2011-07-08
> **wojox said:**
> It's been a while. Look in Gconf-editor > apps > panel > objects > custom_icon. Click in it and set the path to your new icon. Look in /usr/share/pixmaps/ there are some good gnome icons in there.

Make sure to check use_custom_icon as well.

This doesn't make sense, the foot is not a custom icon, its the correct icon.
Its the Ubuntu icon which is the custom icon. I want it gone.

---

### Post by pqwoerituytrueiwoq on 2011-07-08
/apps/panel/objects/menu_bar_screen0/custom_icon
/apps/panel/objects/menu_bar_screen0/use_custom_icon

[alt]+[f2] gconf-editor
browse to those locations

i think Ubuntu tweak can do this now that i think of it

---

### Post by wojox on 2011-07-09
> **Cgenet said:**
> This doesn't make sense, the foot is not a custom icon, its the correct icon.
Its the Ubuntu icon which is the custom icon. I want it gone.

It's Ubuntu. Fedora and openSUSE use gnome and they have their own icons. If you want to use a different icon follow the directions I gave you.

Follow pqwoerituytrueiwoq directions as well. It looks like he's on 10.04 also. I'm not on 10.04 but I've done this several times in the past.

---

