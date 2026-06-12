---
title: "Which directory do themes go into?"
date: 2009-09-29
forum: General Help
---

### Post by j.bell730 on 2009-09-29
I seem to have forgotten what directory installed themes go into. My Gnome Appearance Properties window is constantly crashing, so I need to install this theme manually.
So, which directory am I supposed to move the theme to?

---

### Post by undecim on 2009-09-29
themes are stored in the .themes folder in your home directory, or in /usr/share/themes/.

Though to set your theme, you have to edit the settings with gconf-editor.

Press ALT+F2 and type "gconf-editor". When the editor opens, go to the /desktop/gnome/interface/ directory

Change the "gtk_theme" key to your desired gtk (window controls) theme, "icon_theme" to your desired icon theme, etc...

---

### Post by j.bell730 on 2009-09-29
Thanks, got it :).

---

