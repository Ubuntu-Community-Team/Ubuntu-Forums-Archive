---
title: "Login resolution too low"
date: 2010-05-21
forum: General Help
---

### Post by Dreigo42 on 2010-05-21
I have Ubuntu 10.04 amd64 on a custom machine and works beautifully.....except for the login screen. I have the normal resolution set at 1152x864 60hz and the login screen looks like it is at 800x600. The menus at the bottom overlap and everything is a mess. User resolutions are fine but I like Gnome but my wife likes KDE so we switch it back and forth. Does anybody have a fix?

AMD Dual-Core
ATI Radeon HD1450 w/ restricted drivers enabled

---

### Post by lykwydchykyn on 2010-05-21
Can you post the contents of /etc/X11/xorg.conf, if it exists?

---

### Post by Dreigo42 on 2010-05-21
Sure


Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "fglrx"
EndSection

---

### Post by lykwydchykyn on 2010-05-21
Try this:
1. backup the current file:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-old

```

2. Edit xorg.conf as root
```

gksudo gedit /etc/X11/xorg.conf

```

3. After the line "DefaultDepth 24" and before the line "EndSection", add this:
```

SubSection     "Display"
        Depth       24
        Modes      "1152x864"

```

4. Save, and then reboot (or log out and select "restart X server" from the action menu).

---

### Post by Dreigo42 on 2010-05-21
Sweet thanks!

---

