---
title: "Remote Desktop Problem"
date: 2010-03-04
forum: General Help
---

### Post by Mistrblank on 2010-03-04
I used to use RealVNC viewer to connect to my Ubuntu hosts remotely after activating Remote Desktop.  

After updating to 9.10 (from 8.10) I lost the ability to do that.  I've even tried installing a fresh 9.10 and trying to connect to that and seem to get the same issue. 

Is there anything I need to know about vnc access on the newer release that I need to change for my viewer to connect?

---

### Post by lavinog on 2010-03-05
The settings may have changed between releases...check system>preferences>remote desktop
and see that you have allow other users to view your desktop enabled.

---

### Post by jmichelsen on 2010-03-05
Do you get any kind of an error? Have you verified that vnc server is running on the ubuntu machine? It could be just about anything, going from what you said but I would wager a guess at firewall or changed vnc server config causing it not to start..

---

### Post by HermanAB on 2010-03-05
Howdy,

You should do yourself a huge favour and start to use SSH instead of VNC.  VNC is mostly a Windows thing, it is hard to get to work and you don't really need it. SSH can do everything VNC does and much, much more.

---

### Post by lavinog on 2010-03-05
> **HermanAB said:**
> Howdy,

You should do yourself a huge favour and start to use SSH instead of VNC.  VNC is mostly a Windows thing, it is hard to get to work and you don't really need it. SSH can do everything VNC does and much, much more.

Does ssh allow sharing of a desktop?

Your statement seems more like you are trying to convince the OP to use the terminal for everything and forget the desktop.

---

