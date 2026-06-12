---
title: "Missing my themes"
date: 2009-12-06
forum: General Help
---

### Post by Ancanus on 2009-12-06
[B]Ubuntu 9.10 Karmic Koala
[/B]

_SITUATION:_
I go to System -> Preferences -> Appearance.
The Theme tab is missing all the themes (clearlooks, human, etc.)

I have no idea how this happened. 

[U]
PACKAGE SANITY TEST:[/U]
**gnome-theme **is installed.
**ubuntu-desktop** is installed.

_SOLUTION:_
```
cp -R /usr/share/themes ~/.themes
```

---

### Post by lidex on 2009-12-06
Use nautilus to check contents of "/usr/share/themes" and "/home/your_username/.themes" and check file permissions.

---

### Post by Ancanus on 2009-12-06
/usr/share/themes had all the themes.
~/.themes was empty.

I copied all the themes from /usr/share/themes to ~/.themes and it's working again.

Thanks! :)

---

