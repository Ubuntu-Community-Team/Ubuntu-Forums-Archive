---
title: "Pidgin running in background in Ubuntu Natty"
date: 2011-08-03
forum: General Help
---

### Post by hojjat on 2011-08-03
In Ubuntu Natty with Unity desktop, how can I close the Piding window such that the program will continue to run in the background and I will get notifications when someone sends me a PM?

---

### Post by hojjat on 2011-08-08
Bump?

---

### Post by SalHelder on 2011-08-08
Go to Tools > Preferences. In the Interface tab look for "Show system tray icon:" And set it as Always. Now it will show an icon in the notification area and it will keep running with the window closed.

---

### Post by hojjat on 2011-08-08
I set it to Always, but the icon was not shown in the notification area. Do you have any idea why?

---

### Post by SalHelder on 2011-08-08
I don't, unless... Does it show up in the drop down menu when you click in the your username? To be sure, are you running Unity or Unity 2d?

---

### Post by hojjat on 2011-08-08
I am running Unity. And it turns out this is because pidgin's icon is not in the white-list of notification area icons. Running this command:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```

Fixed the issue.

---

