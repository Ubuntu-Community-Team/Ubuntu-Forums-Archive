---
title: "Work space bar"
date: 2011-07-23
forum: General Help
---

### Post by stevennlv on 2011-07-23
I right clicked my work spaces bar and closed it. Turns out I need it after all, but I haven't been able to find the setting to get it back.

Anybody know where it is?

---

### Post by Frogs Hair on 2011-07-23
Right click the panel > add to panel and select it from the menu or enter this code in the terminal to restore panel applets to default .```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by stevennlv on 2011-07-23
> **Frogs Hair said:**
> Right click the panel > add to panel and select it from the menu or enter this code in the terminal to restore panel applets to default .```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```


Neither option worked for what I need.

Opt  1) did put the switch in the panel, but I need the actual bar back. When I minimize programs they disappear now, since they have "nowhere" to go.

Opt 2) did nothing except make my desktop "blink". I even rebooted (old win habit). But no go.

I see the code was for the gnome config tool. Is there someplace I can edit it manually?

---

### Post by Frogs Hair on 2011-07-23
I was thinking work space switcher . Right click in the area of the top or bottom panel and select add / new panel . You can either add the panel applets from the add to panel menu as I wrote or try the command again when the panel appears .

---

### Post by stevennlv on 2011-07-23
I had to add "Window List" (Switch between open windows with buttons) to get it to work. Maybe we're on different versions?

But thanks for pointing me in the right direction.

---

### Post by Frogs Hair on 2011-07-23
Window list displays open applications and work space switcher allows for the use of different work spaces in Gnome .

---

