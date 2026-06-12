---
title: "I broke something........."
date: 2009-06-30
forum: General Help
---

### Post by jmurch on 2009-06-30
My setup is as follows:

T61 laptop
Ubuntu 9.10
2.6.30-10 kernel

Everything was almost working good but the colors in VLC where gone. I changed the nvidia driver in 'hardware drivers' from ver 180 to ver 173. After reboot it will no longer boot to the GUI.  On boot it gives the error that it's running in low resolution.  I select boot to CLI.  I login, type startx, and it's fine, almost.  I no longer have permissions to run synaptic and I'm sure other things.

Does anyone have any idea what I broke and how I can fix it?

TIA, Jeff

---

### Post by t4thfavor on 2009-06-30
using dpkg reconfigure your xserver, and then try not to break it again...

if you really said 9.10 you are using alpha/beta code, and it cannot be trusted. I suggest sticking to a released version of the os or filing every bug report you can reprouce.

---

### Post by 3rdalbum on 2009-07-01
I wouldn't be surprised if the 173 driver doesn't work with the new Xorg in Ubuntu 9.10.

Instead of typing "startx", type "sudo gdm". You should now be able to access Synaptic and other things. You should try installing the absolute latest Nvidia driver from [www.nvidia.com](www.nvidia.com) to solve your colours problem.

---

