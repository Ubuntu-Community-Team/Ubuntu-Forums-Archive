---
title: "Menu item doesn't execute..."
date: 2011-10-02
forum: General Help
---

### Post by zer010 on 2011-10-02
I just got Cube2: Sauerbraten. It cam e in a bzip file. I can execute the script to run it just fine.  I also have AssaultCube and it comes the same way.  AC had a bash script to add it to the Games category in the Menu.  I found the AC entry in ~/.local/share/applications.  So I copied that and reworked it to point to Sauerbraten and an icon.  It seemed to work great, the menu item is added, icon and all. However, when I select it from the menu, nothing happens.  
Here's what the file, ~/.local/share/applications/cube2:sauerbraten.desktop, looks like: 

```
[Desktop Entry]
Version=0.4
Type=Application
Encoding=UTF-8
Exec=/home/zer0/Games/sauerbraten/sauerbraten_unix.sh
Icon=/home/zer0/Games/sauerbraten/data/cube.png
StartupNotify=false
Categories=Game;ActionGame;
Name=Cube2:Sauerbraten
Comment=Fast paced first-person shooter and game engine.
```

This works fine for AC, but I'm not getting any luck with Cube2... Any ideas?

---

### Post by zer010 on 2011-10-03
Perhaps this thread should be moved to "Desktop Environments"....^_^?

---

