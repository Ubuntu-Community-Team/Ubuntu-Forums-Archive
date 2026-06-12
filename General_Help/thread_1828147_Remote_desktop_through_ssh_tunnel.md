---
title: "Remote desktop through ssh tunnel"
date: 2011-08-18
forum: General Help
---

### Post by electriceddy on 2011-08-18
Hi All,

When I view a work computer Remote Desktop settings it states that connections are only available to other computers on the LAN.

I've managed to connect to the work computer from home via another work computer on the remote site as follows:

ssh root@work-pc1 -L 5050:work-pc2:22

ssh administrator@localhost 5050

This gives me a terminal window on the work pc2.

Is there any way I can start a Remote Desktop session on pc2 through the ssh port forwarded session?

Patrick.

---

### Post by Irony on 2011-08-18
I use Putty and Remmina.

---

### Post by electriceddy on 2011-08-19
Is there any way to use the Remote Desktop Viewer which is already available as a menu item?

Patrick

---

### Post by electriceddy on 2011-08-19
> **salemeni said:**
> Try ssh with X11Forwarding

As in using the -X option when I setup the ssh port forwarding tunnel?  I tried that but nothing happened.  Maybe because the DISPLAY was exported to 0.0

Patrick

---

