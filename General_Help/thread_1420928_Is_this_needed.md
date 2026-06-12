---
title: "Is this needed ?"
date: 2010-03-03
forum: General Help
---

### Post by jmore9 on 2010-03-03
I noticed that gnome remote desktop server has been enabled at startup.  Is this needed for just a desktop ?

Thanks for any help in advance.

---

### Post by collinge on 2010-03-03
mine has been disabled for a while now... runs fine

---

### Post by jmore9 on 2010-03-03
OK Good enough for me.  I just like to ask questions first.  Always better to ask a question and not get answer then to not try at all.

---

### Post by doas777 on 2010-03-03
you don't need it unless you want to control the PC remotely (within your local network).
it's safe to disable otherwise.

---

### Post by kyletstrand on 2010-03-03
I'm pretty sure I know the answer to this already, but I'm still an Ubuntu newb...but is it required to run Ubuntu on both PCs on the network to be able to access the Gnome remote desktop or would I be able to access my Ubuntu desktop from XP?

I believe the answer it is needed, but I don't know and I'm curious.

---

### Post by doas777 on 2010-03-04
> **kyletstrand said:**
> I'm pretty sure I know the answer to this already, but I'm still an Ubuntu newb...but is it required to run Ubuntu on both PCs on the network to be able to access the Gnome remote desktop or would I be able to access my Ubuntu desktop from XP?

I believe the answer it is needed, but I don't know and I'm curious.


well, first off, "remote desktop" means very differant protocols on ubuntu and windows systems. ubuntu's remote desktop is based on VNC. as such you can connect to an ubu system running remote desktop, from windows/ubuntu with a vnc client like tightvnc or realvnc. this however is only true if the service is running, as I'm sure you have guessed. the MS remote desktop runs on the RDP protocol (formerly MS terminal services), so to access an XP systems remote desktop from ubu, use Applications -> Internet -> Terminal Services Client.

HTH

---

