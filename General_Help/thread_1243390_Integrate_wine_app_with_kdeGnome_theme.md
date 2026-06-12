---
title: "Integrate wine app with kde/Gnome theme"
date: 2009-08-18
forum: General Help
---

### Post by praveesh on 2009-08-18
Is there any way to integrate the wine apps in the kde/Gnome desktop environment? . I mean by integration is that the apps in wine and the native linux apps having the same theme. Thanks.

---

### Post by CatKiller on 2009-08-18
**winecfg**

Graphics &#8594; "Allow the window manager to control the windows" & "Allow window manager to decorate the windows."

Widgets inside the windows (icons, toolbar elements, and so on) will still be controlled by the application itself, though.

---

### Post by praveesh on 2009-08-18
> **CatKiller said:**
> **winecfg**
Graphics &#8594; "Allow the window manager to control the windows" & "Allow window manager to decorate the windows."
Widgets inside the windows (icons, toolbar elements, and so on) will still be controlled by the application itself, though.
 Thanks but what I wish is the widgets inside the window to be decorated by the Gnome theme.

---

### Post by CatKiller on 2009-08-18
> **praveesh said:**
> Thanks but what I wish is the widgets inside the window to be decorated by the Gnome theme.

That can only work if you're using a GTK+ application.

---

### Post by praveesh on 2009-08-18
I have heard that the cross over does the job. I don't know whether it is right or not.

---

### Post by CatKiller on 2009-08-18
Nor do I. I've never used it.

---

