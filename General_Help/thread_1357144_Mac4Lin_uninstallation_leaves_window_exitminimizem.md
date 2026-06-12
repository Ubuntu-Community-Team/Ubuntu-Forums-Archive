---
title: "Mac4Lin uninstallation leaves window exit/minimize/maximize buttons in top left"
date: 2009-12-16
forum: General Help
---

### Post by RonB123123 on 2009-12-16
Hi. I installed Mac4Lin, tried it out, created problems with some of my programs so I ran the uninstall shell file and gave it super user access. It said it uninstalled completely, but the normal buttons on the top right in gnome were moved to the top left of the every window and after the uninstallation, the buttons have not moved back to the top right.

I looked on the Mac4Lin sourceforge page and couldn't find any help there. Is there a way to revert my theme back to Human-Clearlooks? I already set that in my Appearance settings and it looks like ubuntu but with this minor annoyance of exit/min/max on the left side instead of the right side.

Is there a way to reset my theme or revert it back to normal?

Thanks,
Ron

Edit: Fixed in this topic. 
[http://ubuntuforums.org/showthread.php?t=921500](http://ubuntuforums.org/showthread.php?t=921500)

Run this command.
> 
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"


---

### Post by RonB123123 on 2009-12-17
.

---

### Post by RonB123123 on 2009-12-19
.

---

### Post by JonasJh on 2009-12-19
> **RonB123123 said:**
> Hi. I installed Mac4Lin, tried it out, created problems with some of my programs so I ran the uninstall shell file and gave it super user access. It said it uninstalled completely, but the normal buttons on the top right in gnome were moved to the top left of the every window and after the uninstallation, the buttons have not moved back to the top right.

I looked on the Mac4Lin sourceforge page and couldn't find any help there. Is there a way to revert my theme back to Human-Clearlooks? I already set that in my Appearance settings and it looks like ubuntu but with this minor annoyance of exit/min/max on the left side instead of the right side.

Is there a way to reset my theme or revert it back to normal?

Thanks,
Ron

If you dont use emerald this should work.

open terminal write 

```
gconf-editor
```

go apps>metacity>general

and find button_layout

It will stand 

```
close,minimize,maxmize:menu
```

as value. change this to

```
menu:minimize,maximize,close
```

and press enter. Done.

Heh. My first post. Im orginaly debian user..

---

### Post by RonB123123 on 2009-12-19
Thanks Jonas. It worked great for me! Welcome to ubuntuforums. :)

---

