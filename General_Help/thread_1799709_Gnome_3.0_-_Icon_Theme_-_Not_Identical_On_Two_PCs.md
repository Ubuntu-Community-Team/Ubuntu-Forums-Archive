---
title: "Gnome 3.0 - Icon Theme - Not Identical On Two PCs?"
date: 2011-07-08
forum: General Help
---

### Post by Roasted on 2011-07-08
Two systems:

Netbook

Custom Desktop

Both on Ubuntu 11.04.
Both using Gnome 3 PPA with Gnome Shell.
Both using the same icon themes.

However on my desktop, when I have an icon theme it always changes the icons in the quick launch within the Gnome Shell dash on the left side. However, a lot of the icon themes on my netbook do NOT change the icons within the dock in the dash. Some themes, like Nostromo, change it fine. Others, like F-Darkest-Colors-Black (Faenza) do not.

Any ideas?

All icons are stored in /home/me/.icons. I own the folders recursively with 755 permissions.


EDIT - The problem was I didn't realize I had so many themes installed that I had the "patch" to the theme. By default, Faenza has some NICE icons, but the folder icons are very bright and their tan color looks a bit strange on my gray-ish theme. F-Dark is a patch to Faenza, which replaces those folder icons with dark gray folder icons. I should have read the darn description, because F-Dark specifies you need Faenza installed for F-Dark to work 100%. Duur... Fixed!

---

