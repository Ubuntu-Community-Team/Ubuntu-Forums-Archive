---
title: "Transparent Application Headers/ window borders??"
date: 2009-10-27
forum: General Help
---

### Post by meinvateristnein on 2009-10-27
is there any way to make transparent window border or even opaque just like vista or 7??

---

### Post by konqueror7 on 2009-10-27
you need compiz and emerald, just follow the link...[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by lovinglinux on 2009-10-27
> **konqueror7 said:**
> you need compiz and emerald, just follow the link...[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Then install this theme...

[http://www.gnome-look.org/content/show.php/Who+Needs+Windows+7+%3F?content=105399](http://www.gnome-look.org/content/show.php/Who+Needs+Windows+7+%3F?content=105399)

---

### Post by meinvateristnein on 2009-10-27
i LIKE the ubuntu theme i just want the top bar / window borders which are black for me to be opaque or 20% transparent!! plz help with this it is driving me crazy

PS. I am Very sure that there is a code just like the one for transparent menus that can be typed into Compiz-manager to give this effect ......... ex. (transparent menus) = Tooltip | Menu | PopupMenu | DropdownMenu Val=80

GET WHAT I AM SAYING???

---

### Post by mcduck on 2009-10-27
> **meinvateristnein said:**
> i LIKE the ubuntu theme i just want the top bar / window borders which are black for me to be opaque or 20% transparent!! plz help with this it is driving me crazy

PS. I am Very sure that there is a code just like the one for transparent menus that can be typed into Compiz-manager to give this effect ......... ex. (transparent menus) = Tooltip | Menu | PopupMenu | DropdownMenu Val=80

GET WHAT I AM SAYING???

No, there's no such code since the transparency plugin works based on what's running inside the window, not the window itself.

But if you want transparent window borders you have two options:

1. If you are using Metacity themes (the default in Ubuntu), press Alt-F2 and run "gconf-editor". Use that to browse to apps/gwd, and you'll find options for adjusting the transparency of active & inactive windows, and for selecting between using the same opacity for the whole border or fading from opaque to the set transparency.

2. Install Emerald, and set Compiz to use it as the default decorator (change the command under Window Decoration-plugin's settings). Emerald themes are actually made to do transparency (unlike Metacity themes), so they will give you much nicer transparency effects and more control over it.

---

### Post by dj-toonz on 2009-10-27
You can get that feature if you install ubuntu-tweak & then in ubuntu-tweak, in Desktop,Windows, u can change the opaque for both active & inactive windows, is that what you mean?

---

### Post by meinvateristnein on 2009-10-27
OMG thankyou to the last two posters and i hope UF has a good day...

---

