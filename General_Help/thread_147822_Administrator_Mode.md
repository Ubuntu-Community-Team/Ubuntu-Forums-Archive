---
title: "Administrator Mode"
date: 2006-03-20
forum: General Help
---

### Post by Linkhiei on 2006-03-20
Umm can anyone tell me how to get into Administrator mode without actually pressing the button? Cuz on my internet setup page its messed up or something and i cant see the admin mode button.

---

### Post by rfruth on 2006-03-20
"sudo -s" from the command line, for more info see the wiki [https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29]("https://wiki.ubuntu.com/RootSudo?highlight=%28sudo%29")

---

### Post by Jucato on 2006-03-20
Your options:
1. run system settings as root
```
kdesu systemsettings
```
2. kcontrol (network settings will have a scroll bar to let you scroll down to the administrator mode button)
```
kcontrol
```
3. run kcontrol as root (similar to running systemsettings as root)
```
kcontrol
```

Please refrain from logging in as root (whether command line or GUI) if there is no need to. If you ever absolutely need to log in as root (with sudo -s or something), please do not forget to log out.

---

