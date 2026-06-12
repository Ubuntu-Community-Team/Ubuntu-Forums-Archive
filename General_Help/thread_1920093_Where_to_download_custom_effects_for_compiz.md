---
title: "Where to download custom effects for compiz?"
date: 2012-02-04
forum: General Help
---

### Post by SAIYANPRINCE on 2012-02-04
I cant seem to find anything otehr than the ones from the standard package and the extra package. If anyone can tell me where to get even more effects, maybe a website or what to search in the spm,  that would be great thanks.

---

### Post by MG&amp;TL on 2012-02-04
```
michael@laptop-testing:~$ apt-cache search compiz | grep plugin
compiz-fusion-plugins-main - transitional dummy package.
compiz-plugins - OpenGL window and compositing manager - plugins
compiz-plugins-default - OpenGL window and compositing manager - default plugins
compiz-plugins-main - Compiz plugins - main collection
compiz-plugins-main-default - Compiz plugins - main default collection
compiz-plugins-main-dev - Compiz plugins - main collection development files
libcompizconfig0 - Settings library for plugins - OpenCompositing Project
libcompizconfig0-dev - Development file for plugin settings - OpenCompositing Project
compiz-fusion-plugins-extra - transitional dummy package.
compiz-plugins-extra - Collection of extra plugins from OpenCompositing for Compiz
compizconfig-backend-kconfig - KConfig Settings library for plugins - OpenCompositing Project
utouch-compiz - uTouch plugin for compiz
michael@laptop-testing:~$ 

```

IDK how many of those you have....:)

Have fun, but if you're using compiz  on a release with Unity, make sure to read [this guide]("https://help.ubuntu.com/community/CompositeManager") before starting.

---

### Post by SAIYANPRINCE on 2012-02-04
> **MG&TL said:**
> ```
michael@laptop-testing:~$ apt-cache search compiz | grep plugin
compiz-fusion-plugins-main - transitional dummy package.
compiz-plugins - OpenGL window and compositing manager - plugins
compiz-plugins-default - OpenGL window and compositing manager - default plugins
compiz-plugins-main - Compiz plugins - main collection
compiz-plugins-main-default - Compiz plugins - main default collection
compiz-plugins-main-dev - Compiz plugins - main collection development files
libcompizconfig0 - Settings library for plugins - OpenCompositing Project
libcompizconfig0-dev - Development file for plugin settings - OpenCompositing Project
compiz-fusion-plugins-extra - transitional dummy package.
compiz-plugins-extra - Collection of extra plugins from OpenCompositing for Compiz
compizconfig-backend-kconfig - KConfig Settings library for plugins - OpenCompositing Project
utouch-compiz - uTouch plugin for compiz
michael@laptop-testing:~$ 

```

IDK how many of those you have....:)

Have fun, but if you're using compiz  on a release with Unity, make sure to read [this guide]("https://help.ubuntu.com/community/CompositeManager") before starting.

I'm using gnome not unity.

I don't quite understand how to install all those packages you quoted, do I search them up in the spm??

---

### Post by MG&amp;TL on 2012-02-04
spm?

GNOME 2, or GNOME 3?

Simply search for compiz plugins in the software centre. If you already have compiz-fusion-plugins extra, compiz-plugins, and compiz-plugins-extra, then that's about it. You can download the source of some new ones off the compiz website, but that's quite difficult.

---

### Post by SAIYANPRINCE on 2012-02-04
> **MG&TL said:**
> spm?

GNOME 2, or GNOME 3?

Simply search for compiz plugins in the software centre. If you already have compiz-fusion-plugins extra, compiz-plugins, and compiz-plugins-extra, then that's about it. You can download the source of some new ones off the compiz website, but that's quite difficult.

okay thanks

---

