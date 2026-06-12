---
title: "theme.index file install?"
date: 2011-05-22
forum: General Help
---

### Post by galacticaboy on 2011-05-22
I have a theme for Xubuntu 11.04 I would like to install. How would I do it, I have a Metacity-1 folder, a GTK-2.0 folder, and a theme.index file. What do I do?

---

### Post by gsmanners on 2011-05-22
Themes go into your ~/.themes folder (so create that if it doesn't exist, first).

So, for example, your gtkrc would go into:

```
~/.themes/myTheme/gtk-2.0/
```

Xubuntu doesn't use Metacity, so you'll have to find Xfwm themes.

see: [http://xfce-look.org/](http://xfce-look.org/)

---

### Post by galacticaboy on 2011-05-22
> **gsmanners said:**
> Themes go into your ~/.themes folder (so create that if it doesn't exist, first).

So, for example, your gtkrc would go into:

```
~/.themes/myTheme/gtk-2.0/
```

Xubuntu doesn't use Metacity, so you'll have to find Xfwm themes.

see: [http://xfce-look.org/](http://xfce-look.org/)

I have done that, then when I go to change it, they never show up.

---

### Post by gsmanners on 2011-05-22
Themes in Appearance are in the "gtk-2.0" folder, and themes for Window Manager go in the "xfwm4" folder. Otherwise, it's just as I pointed out.

---

### Post by galacticaboy on 2011-05-22
> **gsmanners said:**
> Themes in Appearance are in the "gtk-2.0" folder, and themes for Window Manager go in the "xfwm4" folder. Otherwise, it's just as I pointed out.

Thanks!

---

