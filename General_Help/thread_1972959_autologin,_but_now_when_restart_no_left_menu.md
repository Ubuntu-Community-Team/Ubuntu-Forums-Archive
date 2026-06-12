---
title: "autologin, but now when restart no left menu"
date: 2012-05-04
forum: General Help
---

### Post by qwertyjjj on 2012-05-04
I was trying to set up 11.10 for autologin through system settings.
So, I managed to do that but now when I restart I have no left hand menu.
All I can see on the top is file, edit, view, go, bookmarks, help.
Any ideas how I can restore all of the normal menus?

---

### Post by qwertyjjj on 2012-05-05
Ok, I solved this by doing:

> 
gksudo gedit /etc/lightdm/lightdm.conf
remove the line: autologin-user= YOUR USERNAME
Restart computer with: sudo shutdown -h now


But why is autologin causing these problems?

---

