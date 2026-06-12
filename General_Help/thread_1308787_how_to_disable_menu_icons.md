---
title: "how to disable menu icons?"
date: 2009-10-31
forum: General Help
---

### Post by pjomega on 2009-10-31
So it seems that karmic/gnome 2.28 has cause quite a bit of confusion over menu icons. It used to be that you enabled all menu/button icons or disabled them in system/preferences/appearances or the appropriate key in gconf. It seems that the new gnome "disables" them by default and whitelists a few that show up regardless. So the newbies get confused when half their icons disappear and they don't know how to enable them. And those of us that *HATE* icons can't seem to disable them, since the control panel and the menus_have_icons key don't disable all of them. I've seen two threads on this, marked [Closed] with no answer.

So, has anyone found a way to disable all the menu icons?

---

### Post by bibekdai on 2009-10-31
right click on desktop > change desktop background > interface > untick show icons in menus

---

### Post by pjomega on 2009-10-31
That just brings up gnome-appearance-properties, which like i posted, doesn't fix the problem. It removes icons from general menus but the main gnome menu, among others, still has icons regardless of whether it's ticked or not.

---

### Post by nutellajunkie on 2010-12-19
BUMp!

---

### Post by tredegar on 2010-12-20
gconf-editor
desktop
gnome
interface
menus_have_icons - [uncheck]
Close

---

