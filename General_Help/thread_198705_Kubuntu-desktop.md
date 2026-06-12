---
title: "Kubuntu-desktop"
date: 2006-06-17
forum: General Help
---

### Post by _simon_ on 2006-06-17
Hi,

I thought I'd finally give KDE a try so I downloaded and installed the Kubuntu-desktop and all its dependencies.

When I start a KDE session I get 2 errors - see screenshots

What do I need to do?

I have added the following into xorg.conf and restarted but it's had no effect.

```

Section "Extensions"
 Option "Composite" "Enable"
EndSection

```

I'm not sure what it's actually referring to when it says transparency as I've just selected transparency on the panel and it works fine...

---

### Post by AirRaven on 2006-06-17
Try disabling XGL/Compiz.

---

### Post by Jucato on 2006-06-17
Actually, just try disabling shadows/translucency for windows (that's what it's complaining about).
Launch System Settings (Alt+F2, type in "systemsettings"), click on Desktop, then Window Behavior, and in the Translucency tab, uncheck/disable "use translucency/shadows".

---

