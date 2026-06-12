---
title: "gedit no protocol specifies"
date: 2011-06-25
forum: General Help
---

### Post by jaypatel on 2011-06-25
I am getting following error:
root@jay-laptop:/home/jay# gedit /etc/udev/rules.d/10-udev.rules
No protocol specified

(gedit:4151): Gtk-WARNING **: cannot open display: :0.0

---

### Post by varunendra on 2011-06-25
Please provide more details about your OS version and what you are trying to accomplish.

Your command prompt shows you are logged in as "root". Is this a server or a normal desktop in root session (without GUI)?

I think X server must be running in order to display any GUI window. See this: [http://ubuntuforums.org/showthread.php?t=1000827](http://ubuntuforums.org/showthread.php?t=1000827)

---

### Post by dcstar on 2011-06-25
> **jaypatel said:**
> I am getting following error:
root@jay-laptop:/home/jay# gedit /etc/udev/rules.d/10-udev.rules
No protocol specified

(gedit:4151): Gtk-WARNING **: cannot open display: :0.0

gedit is a GUI text editor, use a non-GUI app:

```
**nano** /etc/udev/rules.d/10-udev.rules
```

---

