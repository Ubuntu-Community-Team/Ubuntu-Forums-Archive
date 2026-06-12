---
title: "How do I open TCP/UDP ports??"
date: 2009-07-20
forum: General Help
---

### Post by jerealva on 2009-07-20
Hello :smile:

After some research I found that all I need to do to fix Diablo 2 to host a network game is to "Open outbound and inbound, TCP and UDP, port 6112 and 4000." Now if only I knew what that meant, hehe.

Anyone know where I would go to do that? 

Thank you!
Jerm

---

### Post by arkara on 2009-07-20
you can open them via your router.
just type 192.168.1.1 on your browser and use the manual
of your router.

---

### Post by YesSir on 2009-07-20
To open the ports on your host you can use firestarter (in case you don´t know how to open the ports using the command line). To open the ports on your router, 192.168.1.254 might also be the address, depending on the make of the router (indeed, consult the manual).

---

### Post by Cheesemill on 2009-07-20
[www.portforward.com](www.portforward.com)

---

### Post by jerealva on 2009-07-20
Thank you for the help guys!

---

### Post by The Cog on 2009-07-20
> **YesSir said:**
> To open the ports on your host you can use firestarter (in case you don´t know how to open the ports using the command line). To open the ports on your router, 192.168.1.254 might also be the address, depending on the make of the router (indeed, consult the manual).

This is not right. If the poster hasn't installed a firewall, then no ports are being blocked by a firewall. There is no need to install a firewall (whos job it is to block ports) just so you can reconfigure it to unblock the ports again. That's just building a wall in order to be able to knock a doorway in it.

If he already has a firewall installed, then of course he will have to reconfigure it to allow the necessary ports. But my guess is that he hasn't installed a firewall already.

---

