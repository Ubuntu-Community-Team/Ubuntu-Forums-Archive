---
title: "Classic gnome automatically  on 11.10?"
date: 2011-12-05
forum: General Help
---

### Post by garyed on 2011-12-05
I understand how to get back to classic gnome for a session but I log in automatically & it always logs me in to Unity & I have to re log in to get back to gnome classic. Is there a way to automatically log into gnome classic every session by default?

---

### Post by didinium on 2011-12-05
First go into terminal and type sudo nano /etc/lightdm/lightdm.conf, then change the line user-session=ubuntu to user-session=ubuntu-2d.

---

### Post by garyed on 2011-12-05
> **didinium said:**
> First go into terminal and type sudo nano /etc/lightdm/lightdm.conf, then change the line user-session=ubuntu to user-session=ubuntu-2d.

I tried that & it didn't work

---

### Post by didinium on 2011-12-06
Try this 
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell

---

### Post by garyed on 2011-12-06
> **didinium said:**
> Try this 
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell

That actually worked but for some reason the very top panel on the desktop was unreadable. When I do as the sticky recommends all works & looks fine but it has to be manually done every time at start up or log out & in. Maybe since I choose "Gnome Classic" the line 
```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic
```
might work the same way.

---

