---
title: "change icon for all pdfs in gnome (nautilus)"
date: 2009-08-13
forum: General Help
---

### Post by lorenz_b on 2009-08-13
hi everyone,

is there the possibility to change icons of pdfs in gnome (or nautilus and desktop). right now it is the same icon as with other documents, and not distinguishable at first sight.

cheers,
Lorenz

---

### Post by CatKiller on 2009-08-13
It's theme-dependent. Whether an icon theme has an icon for a given mimetype is dependent on whether the author of that theme bothered to make one, or if it's included in one of the icon themes that that theme inherits.

You can copy (or create, if you're feeling creative) an icon for a given mimetype by putting it in the (appropriately sized) mimetypes directory of the theme you're using. It's probably easiest to copy the icons from another theme that you like into the theme that you're using. Depending on whether it's a per-user theme (~/.icons) or a system-wide theme (/usr/share/icons) the location will be different. You'll need to use root (gksudo nautilus) to be able to change system-wide themes.

I believe the icon for the PDF mimetype is simply called "pdf."

---

