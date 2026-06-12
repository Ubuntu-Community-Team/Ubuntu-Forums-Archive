---
title: "mozilla prism app wont open"
date: 2010-01-12
forum: General Help
---

### Post by phillychease on 2010-01-12
so i made wordpress an app from prism
and i put it in my main menu but i cant open it. i get gedit and it says this
```
#!/usr/bin/env xdg-open

[Desktop Entry]
Name=Wordpress
Type=Application
Comment=Web Application
Exec="prism" -override "/home/phillychease/.webapps/wordpress@prism.app/override.ini" -webapp wordpress@prism.app
Categories=GTK;Network;
StartupWMClass=Prism
StartupNotify=true
Icon=/usr/share/icons/hicolor/48x48/apps/blue-j.png
```

am i suppose to make the app executable?

---

### Post by 3rdalbum on 2010-01-12
Try creating the link again and telling Prism to put it on the desktop. Does this new link work?

---

### Post by phillychease on 2010-01-12
yea it does, but when i add it to the menu and put a icon for it, it just stops working

---

### Post by phillychease on 2010-01-13
*bump*

---

