---
title: "Profiles in gnome-terminal"
date: 2009-09-23
forum: General Help
---

### Post by kurakusan on 2009-09-23
Im using gnome terminal and I was dumb enough to remove the task bar from the top of the window. Now I cant figure out how to edit my profile to change things like the window transparency :(. I thought I might be able to get edit a file to change that stuff but i cant find it.

---

### Post by Tim Sharitt on 2009-09-23
You should be able to restore the menu bar in gconf-editor. Hit Alt+F2 and enter
```
gconf-editor
```

Go to apps > gnome-terminal > profiles and select your profile (most likely Default). Find the entry for show menu bar and check the box beside it.

---

### Post by nothingspecial on 2009-09-23
I think you can just right click the terminal and choose edit profile.

---

