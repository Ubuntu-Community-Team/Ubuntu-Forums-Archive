---
title: "Help File manager autostart loop"
date: 2010-08-04
forum: General Help
---

### Post by Saiph on 2010-08-04
Hallo,
I need help. I have got virus In my computer. After I installed last Win2-7 Pack   5.7.2Multilang Aero!   theme and restart, some script appears , because file manager starting up automaticaly more more times, then slowly closing itself .

In my processes are two without name, so I quick kill one, but starting again, so I put down its priority, now autostart nautilus  disapeared, but nautilus cant start.

I cant run nautilus!

I Install kubuntu desktop then, and all is OK, create new gnome admin user, the same problem, ...  but i want to use gnome. Please help!

UBUNTU LUCID LYNX x64, latest updates installed

Message from terminal:
(nautilus:3352): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:3352): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by Saiph on 2010-08-04
find solution:

sudo gconf-editor
app/nautilus/preferences/show desktop   - tick

I made it from kde not gnome :)

well done hi

---

