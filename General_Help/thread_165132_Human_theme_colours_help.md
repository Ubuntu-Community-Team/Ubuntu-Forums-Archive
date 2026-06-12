---
title: "Human theme colours help"
date: 2006-04-24
forum: General Help
---

### Post by John64 on 2006-04-24
Using the "Theme" preference dialouge i set the controls to clearlooks which changes the colours to blue, and the window borders to human which has the nice new window borders.  This does not get the nice new buttons.

How do i make the Human theme look blue???

---

### Post by croak77 on 2006-04-24
Take a look at [http://www.gnome-look.org/]("http://www.gnome-look.org/").

---

### Post by Nikusan on 2006-04-24
[QUOTE=croak77]Take a look at [http://www.gnome-look.org/]("http://www.gnome-look.org/").[/QUOTE]

Beat me to it. :) 
Two in particular:
[LIST]
[*][Human BC]("http://www.gnome-look.org/content/show.php?content=36566")
[*][Human Blue]("http://www.gnome-look.org/content/show.php?content=36396")
[/LIST]

---

### Post by John64 on 2006-04-24
Well i have downloaded the Human-Blue theme, and it looks great, but Synaptic and a couple other applications look like they are using the Redmond theme

---

### Post by xenmax on 2006-04-24
I could be wrong, but I think that is because they use root theme, not your user theme.

---

### Post by z_diver on 2006-04-24
[quote=John64]Well i have downloaded the Human-Blue theme, and it looks great, but Synaptic and a couple other applications look like they are using the Redmond theme[/quote] This is easily fixed by coying all your themes from [COLOR=Red]~/.themes/[/COLOR] to [COLOR=Red]/usr/share/themes/[/COLOR].  That way the root theme which will follow your settings, has access to the theme you are using.  

HINT: it is not necessary to have themes in both locations.  Just put the extracted themes in [COLOR=DarkRed]/usr/share/themes[/COLOR] and icons and cursors in [COLOR=DarkRed]/usr/share/icons[/COLOR] from now on.  It's much much more complete this way and all the other users of your system benefit at the same time.  I have those two locations bookmarked in my root user's nautilus.

---

### Post by John64 on 2006-04-24
Thanks!

---

