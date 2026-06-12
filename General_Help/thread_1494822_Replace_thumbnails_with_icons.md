---
title: "Replace thumbnails with icons"
date: 2010-05-27
forum: General Help
---

### Post by altonbr on 2010-05-27
For all my .htm, .html and .shtml files, Nautilus runs a thumnailer to preview the file. I disable the thumnailer in gconf-editor at /desktop/gnome/thumbnailers/text@html. Now it's just showing the text inside the file. How do I replace the thumbnail and now the text with just an icon for HTML?

I attached an image that shows the preview thumbnail, text thumbnail, then icon, which is what I want it to look like.

---

### Post by gadolinio on 2010-05-27
> **altonbr said:**
> For all my .htm, .html and .shtml files, Nautilus runs a thumnailer to preview the file. I disable the thumnailer in gconf-editor at /desktop/gnome/thumbnailers/text@html. Now it's just showing the text inside the file. How do I replace the thumbnail and now the text with just an icon for HTML?

I attached an image that shows the preview thumbnail, text thumbnail, then icon, which is what I want it to look like.

Mmm I don't even have text@html there, and my html files have a standard html icon. That makes me wonder whether deleting that entry would do the job. Before that, disabling text preview should do what to want. Alt+F2, type "nautilus-file-management-properties; in the "previwe" tab, change the value for "show text in icons" to "never".

---

### Post by altonbr on 2010-05-27
That's the key, thank you!

Also:
```
gconftool-2 --type string --set /apps/nautilus/preferences/show_icon_text "never"
```

---

### Post by gadolinio on 2010-05-27
> **altonbr said:**
> That's the key, thank you!

Also:
```
gconftool-2 --type string --set /apps/nautilus/preferences/show_icon_text "never"
```

You're welcome.

---

