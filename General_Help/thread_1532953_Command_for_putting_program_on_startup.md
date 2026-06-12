---
title: "Command for putting program on startup"
date: 2010-07-17
forum: General Help
---

### Post by hakermania on 2010-07-17
I know that you can go through System-->Preferences-->Startup Applications and then click Add and add everything I want to , but is there any way to do this with a command?
e.g
puttostart /home/alex/executable
Thx for any help

---

### Post by sisco311 on 2010-07-17
Yes, you have to create a .desktop file in ~/.config/autostart:
```

cat << EOF >> ~/.config/autostart/**name**.desktop
[Desktop Entry]
Type=Application
Exec=**command**
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name=**name**
Comment=**comment**
EOF

```

---

### Post by hakermania on 2010-07-17
Ok thank you very much!

---

