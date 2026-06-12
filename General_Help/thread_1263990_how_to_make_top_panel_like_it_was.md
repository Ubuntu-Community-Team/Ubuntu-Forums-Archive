---
title: "how to make top panel like it was"
date: 2009-09-11
forum: General Help
---

### Post by rhythmiccycle on 2009-09-11
i accidentally deleted to top panel (i thought deleted panel would just delete the clock, i didn't know the whole menu bar is the panel)

i made a new panel and added the clock and the "start" menu thing (ubuntu icon) but the system and places are all in the one menu, i liked it how the default panel was.

how do i get "system" "places" out of the ubuntu menu and be their own menus again?

---

### Post by wojox on 2009-09-11
Add Menu Bar.

---

### Post by Jazzy_Jeff on 2009-09-11
You can also put a notification area up. That is like a system tray.

---

### Post by CatKiller on 2009-09-11
To answer the question in the title,

Alt-F2
gconftool-2 --recursive-unset /apps/panel

Log out and log back in.

This will also reset the bottom panel.

---

### Post by rhythmiccycle on 2009-09-12
> **CatKiller said:**
> To answer the question in the title,

Alt-F2
gconftool-2 --recursive-unset /apps/panel

Log out and log back in.

This will also reset the bottom panel.

thanks, that is what i was looking for

i'm kind of glad is deleted the panel, because now i learned how to customise it. mistakes can lead to great discoveries.

---

