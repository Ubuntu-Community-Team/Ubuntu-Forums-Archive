---
title: "Where IS my clock?"
date: 2011-01-03
forum: General Help
---

### Post by Pedroriel on 2011-01-03
My clock has disappeared, I have no idea why, I I can't add to panel with a right click, or drag applet to the panel. Do any of Ubuntu users, or anyone for that matter, have any suggestions as to how I can get a clock back? Thanks. 
Pedro.

Long live Linux in Melbourne!!:guitar:

---

### Post by TeoBigusGeekus on 2011-01-03
Open terminal and give
```
killall gnome-panel
```
to shut it off and then
```
gnome-panel
```
to turn it on again.

---

### Post by Frogs Hair on 2011-01-03
Try
 ```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

---

### Post by Pedroriel on 2011-01-03
Sorry to be a pest, but will that get rid of all the other stuff on the panel? There is only 5 or 6 things there, just wondering. Also, that code is for the terminal, right? Thanks for the help

---

### Post by TNT1 on 2011-01-03
> **Pedroriel said:**
> Sorry to be a pest, but will that get rid of all the other stuff on the panel? There is only 5 or 6 things there, just wondering. Also, that code is for the terminal, right? Thanks for the help

Don't worry, kill the panel, and reboot/logout and login. Your panel will reset to default and you can add whatever you need to it.

---

