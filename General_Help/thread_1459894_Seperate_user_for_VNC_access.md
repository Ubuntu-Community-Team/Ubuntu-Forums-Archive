---
title: "Seperate user for VNC access?"
date: 2010-04-22
forum: General Help
---

### Post by amp_man on 2010-04-22
I've got a headless fileserver running ubuntu 10.04 that I like to be able to VNC into both remotely and from inside the network. Before anyone says anything about security, I'm well aware the risks (and alternatives, but I can't do them), and have set up source IP filtering and strong passwords to try to minimize them, and this would further minimize them.

Any time I'm accessing my fileserver remotely, it's usually just to hop online to check my gmail, which is blocked at work. What I want to do is leave things alone so that my main user account still automatically logs in, at 1680x1050 res, and fires up the default VNC server, and can be accessed from the internal network. I then want to spawn a second X/Gnome session at boot, auto-login a second, more limited user account, at 1024x768 res, and have that account start up tightvncserver on a different port. Can anyone walk me through that, or point me to some guides to do what I need to?

EDIT: part 2 of this is getting the second user account to have read-only access to the shared files, and no access to the network, while the rest of the network, running various windows/linux verisons, still has full rw access.

---

