---
title: "Remove steam"
date: 2010-02-24
forum: General Help
---

### Post by ccbn on 2010-02-24
Hi i installed playonlinux just to try it out. I decided to uninstall it again. Then i looked at the menu and Wine was still there. I saw had to remove the files using 

```
rm -rf $HOME/.wine
```

```
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm
```

Ok i worked.

Before i uninstalled Wine and playonlinux i tried steam out. Now there is also a shortcut under menu called "menu/steam". How do i remove it. When i try to open it, it says could't find playonlinux(usr/share) something like that.

Thanks in advance

---

### Post by wojox on 2010-02-24
Try right clicking your menu and select Edit Menus and delete it from there.

---

### Post by ccbn on 2010-02-24
Thanks. So simple :P

---

