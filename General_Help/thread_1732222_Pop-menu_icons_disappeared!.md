---
title: "Pop-menu icons disappeared!"
date: 2011-04-18
forum: General Help
---

### Post by 81duz1d0 on 2011-04-18
Hello!

When I right-click somewhere and the pop-menu shows up with options like 'copy', 'paste' and so on it wasn't supposed to be icons in front of these items?
Actually, a lot of applications like Firefox aren't showing icons on their menus!

What could it be?

Thanks

---

### Post by wolfen69 on 2011-04-18
> **81duz1d0 said:**
> Hello!

When I right-click somewhere and the pop-menu shows up with options like 'copy', 'paste' and so on it wasn't supposed to be icons in front of these items?
Actually, a lot of applications like Firefox aren't showing icons on their menus!

What could it be?

Thanks
I don't ever recall seeing icons when I right click something. As far as menu icons go, you can right click **applications** on the panel and select edit menus. Select the apps in question and select properties. Then you can change the icons for them.

---

### Post by 81duz1d0 on 2011-04-18
Hmm no, it's not just the applications menu, every menu that has glyphs (like Firefox' Edit menu, right-click on files/folders) they just don't appear at all

---

### Post by mcduck on 2011-04-18
That's how it's supposed to be. Most menu icons were removed from gnome a few versions ago to reduce visual clutter in menus and bring better attention to those selected items that are still allowed to have icons.

It is still possible to enable icons for all menu items through gconf-editor, but I'm actually pretty sure that copy/paste functions don't have icons even if you do that.

---

### Post by 81duz1d0 on 2011-04-18
i could give it a try... do you know which key should be changed?

---

### Post by 81duz1d0 on 2011-04-18
also there are NO icons at firefox menus or any other application's

---

### Post by 81duz1d0 on 2011-04-18
SOLVED!

Just change it: /desktop/gnome/interface/menus_have_icons to 'true' =D

---

