---
title: "No 3D acceleration or sudo in Gnome"
date: 2010-06-17
forum: General Help
---

### Post by grandmasterflash on 2010-06-17
10.04 - X86_64  I was doing an "apt-get upgrade" when my computer lost power from a storm, apparently my battery backup was dead too.  Computer restarts, Asks if I want to run in low graphics mode since it can't start otherwise.  I booted into low graphics, try to run synaptic to check the vid driver. synaptic said a previous operation didn't complete and that I needed to run "apt-get --configure -a". That operation completes. I ran "apt-get upgrade" and it finishes its upgrades.  After a reboot, there is still no 3D acceleration. I try to open synaptic only to have it tell me authorization fails. In short, I can sudo and gksu from a ssh terminal, but sudo and gksu fail to authenticate when being run in the x-windows/gnome menu. I checked gksu-properties, it's marked as use sudo. I checked /etc/sudoers and that seems normal. So I'm not sure what to check now. Oh, and marking Nvidia, nvidia-kernel, gksu, synaptic for reinstallation didn't make a difference.  So to recap  1. 3d acceleration isn't working. 2. sudo/gksu don't work in the gnome environment. are still both problems and I'm not sure what to do next.

---

### Post by grandmasterflash on 2010-06-17
General update:  This morning, I needed to use the computer.. I tried the nvidia-settings tool. It mentioned that I needed to run "nvidia-config" from a terminal since I didn't have a xorg.conf anymore.  Alt-f2 and "nvidia-config" later, I now have 3D acceleration back as well as the ability to sudo/gksu inside of x-windows/gnome after rebooting.  I don't know what happened, but it's working normally again.

---

