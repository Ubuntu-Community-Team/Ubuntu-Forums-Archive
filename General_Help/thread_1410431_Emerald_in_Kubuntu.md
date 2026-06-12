---
title: "Emerald in Kubuntu"
date: 2010-02-18
forum: General Help
---

### Post by Eragon0605 on 2010-02-18
I just recently moved from Ubuntu to Kubuntu. I like the new look, but I thought the window borders were a little bland, so I installed emerald. I installed the themes that I wanted, but when I click on them, nothing happens. In Ubuntu, I had to press Alt+F2 and enter ```
emerald --replace
```or at least that's what I think it was. I tried that, and it didn't work. How can I fix this on Kubuntu?

---

### Post by n0dix on 2010-02-18
See in the compiz-manager, if the window decoration plugin has the argument emerald --replace, and of course, if it is on.

---

### Post by Zorael on 2010-02-19
Since this is Kubuntu I guess he doesn't have Compiz, unless it's implied as installed.

KWin is both a window compositor and a window decorator, while Emerald is only a compositor that needs a decorator to work. You'd need Compiz (or perhaps xcompmgr) to make the pair.

To reword n0dix, in the Compiz settings manager (**ccsm**), there will be a Window Decorator plugin, in which you can point to the Emerald binary. Then you can tell KDE to use Compiz by heading to System Settings -> Default Applications -> Window Manager, and selecting Compiz in the dropdown menu. You may need the **compiz-wrapper** package for it to show up there.

Then just log out and back in. Compiz should start with Emerald, and plasma should enjoy composited effects (panel transparency, etc).

---

