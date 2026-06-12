---
title: "where are the graphics, icons, images for applications stored"
date: 2009-07-01
forum: General Help
---

### Post by charonred on 2009-07-01
I've installed Cairo-Dock and am adding some new apps to it, but have no idea where the various applications image/icon/graphic is stored in Hardy.

I would like to use the default one for GnuCash; but all Cairo-Dock displays is a question mark, so in Cairo's configuration, I need the path to the GnuCash image/icon/graphic - where do I find these.

---

### Post by CatKiller on 2009-07-01
The icon's called gnucash-icon. You might have a theme-dependent version you can use just by specifying the name. Otherwise, the gnucash-common package puts an icon in /usr/share/icons/hicolor.

---

### Post by charonred on 2009-07-01
Many thanks, just the name worked, but now I also know where other icons are located :)

---

### Post by CatKiller on 2009-07-01
> **charonred said:**
> Many thanks, just the name worked, but now I also know where other icons are located :)

FYI, each theme has an Inherits attribute, which means that if an icon is not available in a given theme, the one from the Inherited theme can be used instead. Each theme, by definition, ultimately Inherits icons from the Hicolor theme. Which is why default icons are put there.

There's more information on how icon themes work [here]("http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html").

---

### Post by charonred on 2009-07-01
ta, will check it later, must get on with setting up accounts package

---

### Post by charonred on 2009-07-02
any idea where the VirtualBox icon is located, I've been all though the 'hicolor' folder and can't find it there.

---

### Post by CatKiller on 2009-07-02
> **charonred said:**
> any idea where the VirtualBox icon is located

There are two; one in /usr/share/pixmaps and one in /usr/share/icons. I'm not sure which one you want to use.

---

### Post by charonred on 2009-07-02
thanks again, wasn't one in icons; using the one in pixmaps, bit fuzzy though, so might work on logo in gimp and make a better one

---

