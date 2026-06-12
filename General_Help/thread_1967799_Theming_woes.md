---
title: "Theming woes"
date: 2012-04-28
forum: General Help
---

### Post by Exüberance on 2012-04-28
I just "upgraded" to Ubuntu 12.04. After trying out Unity again and discovering it to still be broken, I switched back to gnome classic. The first thing I noticed is that the panel's colouring is pretty much objectively ugly.

I managed to fix the mismatched panel by replacing the new Ambiance theme with the Ambiance theme from 11.10... soft of.

If I replace the gtk-widgets.css file, all text turns white for some reason, making everything unreadable. If I replace everything except gtk-widgets.css file, the panel looks fine again, but, as expected, not everything is changed.

In some programs, my right-click menus look like this:
[img]http://i.imgur.com/MeAzt.png[/img]
(how it's supposed to look)

But certain programs (nautilus, for one) still has the menus looking like this
[img]http://i.imgur.com/Y6GxC.png[/img]

I've tried manually editing the css file (since apparently it was decided that editing CSS is more user friendly than the super simple colour chooser in 10.4 :roll:) and replacing every instance of fg_color and bg_color in the Combo Box and Menu places with dark_fg_color and dark_bg_color, but the only thing that did was mess up the gradient for selected items and make the font on the menus turn white.

No matter what I do, I can't seem to get the menus back to having black backgrounds. The only way I could get it to work was making *all* windows have a dark grey background by default, but that makes everything else look terrible.

So... any suggestions for how to get themes to work properly again? There doesn't seem to be any documentation at all about whatever they changed. (I note that there's a new file: gtk-widgets-backdrop.css, but modifying it to use the dark colours had no effect either)

---

### Post by Exüberance on 2012-04-28
Aha! I have begun to figure it out. The reason, in hindsight, was obvious: it didn't have a background colour defined, but instead inherited the default.

To fix the background colour of menus, find the menu section in gtk-widgets.css (line 1031 for me) , then replace
[FONT=Courier New]background-image: none;[/FONT]
with
[FONT=Courier New]background-color: @dark_bg_color;[/FONT]

Of course, more needs to be done (make the text white for that, fix the border colour, etc.) I'll post here again once I get it back to how it was in 11.10.

---

