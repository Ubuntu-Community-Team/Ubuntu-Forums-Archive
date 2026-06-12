---
title: "Changing Folder permissions"
date: 2006-05-24
forum: General Help
---

### Post by GhandiBurger on 2006-05-24
what is the terminal command to change the permissions on folders?

---

### Post by cskeide on 2006-05-24
chmod

"man chmod" for more info

---

### Post by GhandiBurger on 2006-05-24
I'm probably just dense, but I can't figure the modes and stuff. What would be the specific chmod code to make /var/www/apache2-default readable, writeable, and executable for group and others?

---

### Post by catlett on 2006-05-24
You can also do it graphically enter this at the terminal ```
gksudo nautilus
``` This opens the file browser as root. Then browse to the folder you want to change. Right click on it and scroll down the menu to "properties". When the properties window opens, hit on "permissions" Check off the boxes you want to enable i.e. read, write, executable for user,group or root.
Close nautilus. The permissions should be changed, I only had one time it didn't work. It was concerning a mounted external drive. The issue was root didn't own it because the user mounted it.But that aside it should work, It is how I do it.

---

### Post by cskeide on 2006-05-24
[QUOTE=GhandiBurger]I'm probably just dense, but I can't figure the modes and stuff. What would be the specific chmod code to make /var/www/apache2-default readable, writeable, and executable for group and others?[/QUOTE]

This will make the folder readable, writable and executable for all users on the system:
```
sudo chmod 777 /var/www/apache2-default
```

---

