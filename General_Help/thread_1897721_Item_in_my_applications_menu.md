---
title: "Item in my applications menu"
date: 2011-12-19
forum: General Help
---

### Post by fl3x on 2011-12-19
I have an idea in my applications menu, it's the netbeans IDE launcher. I can't find the desktop file in /usr/share/applications nor can i find the netbeans ide on ubuntu software center. I can drag the item from the menu to my browser, letting me download it and get the contents of it: 

```

[Desktop Entry]
Encoding=UTF-8
Name=NetBeans IDE 7.0.1
Comment=The Smarter Way to Code
Exec=/bin/sh "/home/mitchell/netbeans-7.0.1/bin/netbeans"
Icon=/home/mitchell/netbeans-7.0.1/nb/netbeans.png
Categories=Application;Development;Java;IDE
Version=1.0
Type=Application
Terminal=0

```

I removed the actual folder at /home/mitchell/netbeans-7.0.1

That simply resulted in no icon for the item, now I really want it removed even more -.-...

I also tried finding the command "netbeans" in terminal, and I tried doing a search in my cache for the word netbeans, didn't find it. Any ideas?


EDIT: Found it at file:///home/mitchell/.local/share/applications/netbeans-7.0.1.desktop

Didn't realize there was an actual local applications folder, thanks for putting up with my stupidity.

---

