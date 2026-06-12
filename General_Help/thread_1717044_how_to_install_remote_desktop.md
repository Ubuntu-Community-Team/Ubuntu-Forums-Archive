---
title: "how to install remote desktop"
date: 2011-03-29
forum: General Help
---

### Post by onel0ve on 2011-03-29
i have one vps with ubuntu 10.10 os 
i want to install remote desktop on it how to do it ?:confused:

---

### Post by Thund3rstruck on 2011-03-29
Gnome has a built-in remote desktop tool you can use. I think it's in Preferences > Remote Desktop. Or you could install VNC server on it. 

If you need to remote desktop into other computers then install the rdesktop package if its not already installed.

---

### Post by doas777 on 2011-03-29
as a server or as a client?

for a vps, don't use the built in "remote desktop" vnc server, unless you configure it to run over ssh.
instead i recommend freenx/NeatX as they are reasonably secure and perform better than vnc-based services.

---

### Post by onel0ve on 2011-03-30
> **doas777 said:**
> as a server or as a client?

for a vps, don't use the built in "remote desktop" vnc server, unless you configure it to run over ssh.
instead i recommend freenx/NeatX as they are reasonably secure and perform better than vnc-based services.
how to install freenx ?

---

### Post by doas777 on 2011-03-30
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

