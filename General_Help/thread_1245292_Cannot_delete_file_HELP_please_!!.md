---
title: "Cannot delete file HELP please !!"
date: 2009-08-20
forum: General Help
---

### Post by Rick Abraham on 2009-08-20
Hi guys I installed AVG free 8.5 and then ran a command to create a launcher in
Applications --> System Tools
But for some reason AVG still didnt work, so I deleted AVG but it left the launcher
behind in System Tools

How can I delete this file ?????
This was the command I used to create it

sudo gedit /usr/share/applications/avg.desktop

---

### Post by DeMus on 2009-08-20
> **Rick Abraham said:**
> Hi guys I installed AVG free 8.5 and then ran a command to create a launcher in
Applications --> System Tools
But for some reason AVG still didnt work, so I deleted AVG but it left the launcher
behind in System Tools

How can I delete this file ?????
This was the command I used to create it

sudo gedit /usr/share/applications/avg.desktop

Right-click Applications
Choose Edit Menus
In the window choose on the left side the right menu. Then on the right side uncheck the box in front of the program you don't want to see in the menus.

---

### Post by michy99 on 2009-08-20
```
sudo rm /usr/share/applications/avg.desktop
```

---

### Post by Rick Abraham on 2009-08-20
thanks guys your advice worked a treat

---

