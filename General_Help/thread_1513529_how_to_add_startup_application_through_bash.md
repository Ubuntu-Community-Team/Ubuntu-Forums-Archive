---
title: "how to add startup application through bash"
date: 2010-06-19
forum: General Help
---

### Post by jakupl on 2010-06-19
I am trying to write a bast script, and I need the script to add something to the startup applications, so that it runs when the user logs in. Is that possible?

Any help would be appreciated.

---

### Post by sisco311 on 2010-06-19
You have to create .desktop file in ~/.config/autostart/


```
cat << EOF >> ~/.config/autostart/name.desktop
[Desktop Entry]
Type=Application
Exec=**command**
Name=**name**
Comment=**whatever** 
EOF
```

---

### Post by jakupl on 2010-06-19
> **sisco311 said:**
> You have to create .desktop file in ~/.config/autostart/


```
cat << EOF >> ~/.config/autostart/name.desktop
[Desktop Entry]
Type=Application
Exec=**command**
Name=**name**
Comment=**whatever** 
EOF
```

It works perfectly. Thanks a bunch.

---

