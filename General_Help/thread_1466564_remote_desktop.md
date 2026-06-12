---
title: "remote desktop"
date: 2010-04-30
forum: General Help
---

### Post by ottosykora on 2010-04-30
Managed to get the desktop of the ubuntu 10.04 onto my windows xp workstation. 
But, I tried to run for example synaptic this way, but this seems not to be possible, think due to root rights needed.

How to handle this? Is it possible to run synaptic via remote desktop and install programs?

---

### Post by dino99 on 2010-04-30
virtualbox

---

### Post by gradinaruvasile on 2010-04-30
> **ottosykora said:**
> Managed to get the desktop of the ubuntu 10.04 onto my windows xp workstation. 
But, I tried to run for example synaptic this way, but this seems not to be possible, think due to root rights needed.

How to handle this? Is it possible to run synaptic via remote desktop and install programs?

The "Remote Desktop" is misleading in Gnome - it is a plain VNC server. It lets you do everything that you normally can, unlike the actual Remote Desktop from Windows that restricts certain things.

What do you mean by "due to root rights needed"? Installing programs via apt/dpkg needs root rights, but you are asked for your password - to elevate your user rights to superuser rights (aka root) temporarily.

---

### Post by ottosykora on 2010-04-30
when connected to the remote desktop, when selecting synaptic from the menu, error messages are displayed saying something having no rights to do so, no password is asked in opposite when I select synaptic local.

---

