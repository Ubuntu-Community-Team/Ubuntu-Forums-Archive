---
title: "Access folders from my MacBook hard drive in Jaunty"
date: 2009-07-21
forum: General Help
---

### Post by barsofham on 2009-07-21
My MacBook's hard drive is sounding off the death rattle and not starting up. I took it out of my laptop and put it into an external sata drive enclosure. I can access some of the files in Jaunty but I get the "You cannot access this folder because you are not the owner" statement. Is there any way that I can access those folders through Ubuntu? I just need to back up some stuff from it then I don't really give a **** about it. I tried using terminal and cd-ing to the folder but get the same message. I tried ```
sudo cd
``` but to no avail. Thanks for any help!

---

### Post by Idefix82 on 2009-07-21
Try
```
sudo chown $USER:USER /complete/path/to/folder

```

substituting the correct path.

---

### Post by ajgreeny on 2009-07-21
Or if you don't want to change the ownership of the files you should be able to get to them and move or copy them with nautilus with root privileges ```
gksudo nautilus
``` from your ubuntu install.  I don't think your command ```
sudo cd
``` will give you root privileges to the folder you cd to, I'm afraid, thiough I admit that I'm not totally certain.  I will try it out in a second or two.

EDIT:
No I've just tried and the command errors with "*sudo cd: command not found."*

---

