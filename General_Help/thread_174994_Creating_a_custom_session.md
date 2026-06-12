---
title: "Creating a custom session"
date: 2006-05-12
forum: General Help
---

### Post by commodore on 2006-05-12
When I log in throught gdm I get to choose the session type or whatever (failsafe, GNOME...). I compiled a window manager myself but I don't have a session for it. How can I create it?

---

### Post by bluevoodoo1 on 2006-05-12
```
sudo gedit /usr/share/xsessions/nameofWM.desktop
```

paste this in...

```

[Desktop Entry]
Encoding=UTF-8
Name=Name of your WM
Comment=Description
Exec=command to run your WM
Terminal=False
TryExec=command to run your WM
Icon=path to icon
Type=Application

[Window Manager]
SessionManaged=true
```

save it. Then log out and it should be there now.

---

### Post by commodore on 2006-05-13
Wow, that was easy. Thank you!

---

### Post by bluevoodoo1 on 2006-05-15
Alright!

---

