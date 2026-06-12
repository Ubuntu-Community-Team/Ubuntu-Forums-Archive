---
title: "Themes"
date: 2006-06-28
forum: General Help
---

### Post by thunderduck3141 on 2006-06-28
hi all
just wondering how do i fix the "theme" background behind the panel in this shot[ATTACH]11914[/ATTACH]


im taling about behind the window list and the sys tray

---

### Post by nalmeth on 2006-06-28
Open the theme manager and change the "Controls" theme.

It's an annoying bug with some gtk themes, a few of them have it (including clearlooks I think), a few don't.

---

### Post by mcduck on 2006-06-29
Clearlooks should work fine. I only get this problem with pixmap-based GTK themes.

There are some option in gconf-editor for scaling background images in panels, but i'm not sure if they would work when the pics are defined in the theme and not in the panel settings..

I can't tell the exact key as I'm not at my Ubuntu box now, but try lookin under /apps/panel/ if you find it. :)

---

