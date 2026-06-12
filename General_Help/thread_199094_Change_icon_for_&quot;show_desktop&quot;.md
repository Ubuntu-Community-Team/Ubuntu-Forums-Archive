---
title: "Change icon for &quot;show desktop&quot;"
date: 2006-06-18
forum: General Help
---

### Post by Lunar_Lamp on 2006-06-18
I currently have the show desktop 'launcher' on my desktop bar in gnome, but it doesn't have transparency like the other icons on the background due to the art of the icon.  Is there a way to change the icon, as it doesn't change like application launchers.  Alternatively, is it possible to create an 'application launcher' that minimises to desktop, using my own icon?

Additionally, I recollet the little white bars that destroy the asthetics of any transparent bar are not removable *insert grumble*?

---

### Post by woot on 2006-06-18
as for your custom show-desktop icon:

start console:
```
gconf-editor
```

apps-->panel-->applets-->show_desktop_button

-->use custom icon (turn on)
-->custom icon path (fill in)

that should do the trick

as for "Additionally, I recollet the little white bars that destroy the asthetics of any transparent bar are not removable *insert grumble*?"

im curious aswell!

---

### Post by aysiu on 2006-06-18
[QUOTE=Lunar_Lamp]I currently have the show desktop 'launcher' on my desktop bar in gnome, but it doesn't have transparency like the other icons on the background due to the art of the icon.  Is there a way to change the icon, as it doesn't change like application launchers.  Alternatively, is it possible to create an 'application launcher' that minimises to desktop, using my own icon?[/quote] To change the icon, you simply replace the old icon with your new one.

The old icon, if you have a user-installed theme, probably lives in /home/lunarlamp/.icons/themename/size/filesystems/gnome-fs-desktop

.icons is a hidden directory. To see it, just press Control-H.

Otherwise, it'll probably be in /usr/share/icons somewhere.

> 
Additionally, I recollet the little white bars that destroy the asthetics of any transparent bar are not removable *insert grumble*? If they bother you that much, use KDE.

---

### Post by Lunar_Lamp on 2006-06-19
If I'm honest, I think it's the only thing I find that KDE has over gnome - and is most certainly not enough of an issue to change to KDE for.  I'll have to look into the code and see if I can hack it, but I suspect it will be over my head.

---

