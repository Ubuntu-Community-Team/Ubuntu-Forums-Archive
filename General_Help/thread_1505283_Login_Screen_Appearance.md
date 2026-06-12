---
title: "Login Screen Appearance"
date: 2010-06-09
forum: General Help
---

### Post by luceerose on 2010-06-09
As of Lucid, it appears that "Login Screen" in gnome-control-center (System>Administration>Login Screen)
no longer provides the functionality to mess around with the appearance of the login screen. I'm just trying to find a way to change the background image on the login screen. Is there a "new" way of doing it, or a workaround ?

---

### Post by kerry_s on 2010-06-09
run this command & select the wallpaper, i suggest you put the 1 you want in "/usr/share/backgrounds" so it's system accessible.
**gksudo -u gdm dbus-launch gnome-appearance-properties**

if the accessibility feature gets turned on, you can turn it off in preferences-> keyboard

forgot to mention, you can also change the theme, fonts, mouse pointer, etc...

i only did mouse & background on mine.

---

### Post by luceerose on 2010-06-09
Thanks.
That worked beautifully.
I changed the background & fonts.
I'm going to make a launcher on my panel for that.

[SOLVED]
:guitar:

---

