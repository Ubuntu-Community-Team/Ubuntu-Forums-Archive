---
title: "xorgconfig not found?"
date: 2006-05-13
forum: General Help
---

### Post by Dakaru on 2006-05-13
vivi@ubuntu:~$ xorgconfig
bash: xorgconfig: command not found
vivi@ubuntu:~$



Can anybody tell me how to fix that?

---

### Post by 5-HT on 2006-05-13
[LIST]
[*]If you want to edit xorg.conf by hand with any editor you prefer, open:[/LIST]```
/etc/X11/xorg.conf
``` 
e.g., to edit with nano:
```
 sudo nano -w /etc/X11/xorg.conf
``` [LIST]
[*]To edit the file in a more interactive fashion:[/LIST]```
sudo dpkg-reconfigure xserver-xorg
``` 
As always, it's a good idea to make a backup prior to editing any important config file.

Hope that helps.

---

