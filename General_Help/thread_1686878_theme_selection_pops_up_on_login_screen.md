---
title: "theme selection pops up on login screen"
date: 2011-02-13
forum: General Help
---

### Post by mworden88 on 2011-02-13
version 10.04.

copy and pasted something into terminal and now the theme selection menu always pops up at the login screen, how do i get rid of that?

---

### Post by Xia Johan on 2011-02-13
Copy paste this into the terminal:

[COLOR=#C20CB9]**sudo**[/COLOR] [COLOR=#C20CB9]**unlink**[/COLOR] [COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]gdm[COLOR=#000000]**/**[/COLOR]autostart[COLOR=#000000]**/**[/COLOR]LoginWindow[COLOR=#000000]**/**[/COLOR]gnome-appearance-properties.desktop

---

