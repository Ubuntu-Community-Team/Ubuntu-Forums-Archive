---
title: "Editing and installing themes..read only files"
date: 2012-07-11
forum: General Help
---

### Post by Pyridine on 2012-07-11
Hi Guys,

I'd like to edit the themes already installed and install a new theme, but I can't simply put a new theme in the theme folder, or edit the themes/icons already there because it's all read only. This is confusing for an ex-windows user...how do I change the privileges to allow me to edit this stuff without screwing up my computer completely?

Thanks - Pyridine

---

### Post by Frogs Hair on 2012-07-11
If the themes are in the File System usr/share/themes root permission is needed to make changes. This is to protect the system from accidental or deliberate damage. Use following to open nautilus with elevated permissions. With any sudo command a password is required.```
gksudo nautilus
```

You can also place themes or icons in a .themes or .icons folder you have created in home hidden folders. (Ctrl + H or show hidden)In the second case the user can access and change the contents of the folder, but the themes/icons are only available to that user.
Permissions are listed in the files properties.

---

### Post by Pyridine on 2012-07-12
Thank you!!!

---

### Post by lolpenguin on 2012-07-12
Be warned:
The root user, aka superuser, can COMPLETE access to your WHOLE SYSTEM. Be careful when running applications using gksu, gksudo, sudo or su. Make backups of anything you edit!
If you want to install themes, install them to ~/.themes or icons to ~/.icons.
Anything with a "." before its name is hidden. Press Ctrl + H to see them. ~/ is your home folder.

Note that themes installed in your home folder will look like Windows 9x when using gksu/do.

---

