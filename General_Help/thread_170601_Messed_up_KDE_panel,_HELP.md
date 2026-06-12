---
title: "Messed up KDE panel, HELP"
date: 2006-05-04
forum: General Help
---

### Post by jonnyfive on 2006-05-04
I messed up the KDE panel on the bottom of my screen and now I cannot see my open windows on the panel or my 4 different desktops and can no longer access themese and styles because the menu isn't there.

Does anyone know another way to get to the themese and styles? I am hoping that if I change the style the panel will too.

---

### Post by aysiu on 2006-05-04
Alt-F2 ```
kcontrol
```

---

### Post by jonnyfive on 2006-05-04
Thank you! 
I have changed the theme and yet my panel still looks like hell. How do I get it back to default?

---

### Post by aysiu on 2006-05-04
[QUOTE=jonnyfive] 
I have changed the theme and yet my panel still looks like hell. How do I get it back to default?[/QUOTE] This may be a bit extreme, but try this: press Alt-F2 ```
konsole
``` In the terminal window, type ```
mv ~/.kde/share/config ~/.kde/share/config_old
``` Then press Control-Alt-Backspace.

---

### Post by jonnyfive on 2006-05-04
Taa daaa, it worked. You have now earned my love and respect!:D

---

### Post by Al3xanR0 on 2006-05-05
[QUOTE=jonnyfive]I messed up the KDE panel on the bottom of my screen and now I cannot see my open windows on the panel or my 4 different desktops and can no longer access themese and styles because the menu isn't there.

Does anyone know another way to get to the themese and styles? I am hoping that if I change the style the panel will too.[/QUOTE]

Right click on the panel-> click add to panel-> click applet-> click "desktop Previewer & Pager" . Right click on the panel-> click add to panel-> click application-> click Control Center

---

