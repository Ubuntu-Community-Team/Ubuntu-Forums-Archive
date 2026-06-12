---
title: "desktop and or Unity side bar links"
date: 2012-07-19
forum: General Help
---

### Post by Neill_R on 2012-07-19
Ubuntu 12.04 server with ubuntu-desktop installed

I want to run the following commands by clicking on a Unity side bar icon  and/or a desktop icon.


[LIST=1]
[*]gksu gedit&
[*]gksu nautilus&
[*]gksu gnome-system-log&
[/LIST]
currently I have to enter thee above commands into a terminal session. This is a pain. While when I lock the icon to the launcher the command is equivalent to 




[LIST=1]
[*]gedit&
[*]nautilus&
[*]gnome-system-log&
[/LIST]
There is no way I know of to alter the command run from a launcher icon.

---

### Post by Frogs Hair on 2012-07-19
See the thread at the link . I have created a Nautilus Root Launcher but of course the password prompt opens when using gksu or gksudo. You may want to use different icons from the regular icons for those applications. [http://ubuntuforums.org/showthread.php?p=12115364#post12115364](http://ubuntuforums.org/showthread.php?p=12115364#post12115364)

---

### Post by Neill_R on 2012-07-20
Not the solution I was looking for. It's too complicated.

---

### Post by Pand5461 on 2012-07-20
To make a desktop icon for Nautilus make a text file with the following contents:
```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Name=Nautilus (root)
GenericName=File Browser
Comment=File Browser - root permissions
Exec=gksu nautilus
Icon=nautilus
Terminal=false
Type=Application
Categories=Utility;Application;
X-GNOME-Autostart-enabled=false
Hidden=false

```

Name it nautilus.desktop and place in your Desktop folder.
The same for gedit and gnome-system-log.

---

### Post by zombifier25 on 2012-07-20
> **Pand5461 said:**
> To make a desktop icon for Nautilus make a text file with the following contents:
```

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Name=Nautilus (root)
GenericName=File Browser
Comment=File Browser - root permissions
Exec=gksu nautilus
Icon=nautilus
Terminal=false
Type=Application
Categories=Utility;Application;
X-GNOME-Autostart-enabled=false
Hidden=false

```

Name it nautilus.desktop and place in your Desktop folder.
The same for gedit and gnome-system-log.

Also, if you wish you can drag the newly created .desktop file on the Unity Launcher.

---

### Post by Neill_R on 2012-07-20
Thank for the very useful information.

Yes I had already tried that and it sort of works:- but in some cases the icon in the launcher side bar is there but invisible. Where should i look to find documentation on these .desktop files?
also the right click menu to activate is invisible but works is it gray on gray and white on white when selected?

<code>
#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Name=Nautilus (root)
GenericName=File Browser
Comment=File Browser - root permissions
Exec=gksu nautilus
Icon=nautilus
Terminal=false
Type=Application
Categories=Utility;Application;
X-GNOME-Autostart-enabled=false
Hidden=false
<code/>

---

### Post by Neill_R on 2012-07-20
this is a better example at nautilus is already there and CAN'T BE REMOVED

#!/usr/bin/env xdg-open
[Desktop Entry]
Version=1.0
Name=Gnome-system-log (root)
GenericName=Log File Viewer
Comment=og File Viewer - root permissions
Exec=gksu gnome-system-log
Icon=gnome-system-log
Terminal=false
Type=Application
Categories=Utility;Application;
X-GNOME-Autostart-enabled=false
Hidden=false

---

### Post by Pand5461 on 2012-07-21
[Here]("http://developer.gnome.org/integration-guide/stable/desktop-files.html.en") is a tutorial on .desktop files.

---

