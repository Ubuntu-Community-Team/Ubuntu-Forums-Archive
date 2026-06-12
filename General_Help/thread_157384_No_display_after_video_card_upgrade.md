---
title: "No display after video card upgrade"
date: 2006-04-09
forum: General Help
---

### Post by djoefish on 2006-04-09
Need help please! I have installed Ubuntu 5.10 on a second HD (XP of first HD). I recently replaced a Radeon card with a new nvidia 6600, and now X fails to load on the bootup. Do I need to reconfigure and/or install drivers? If so, how do I do this from the command line? 

thanks in advance...

---

### Post by krusbjorn on 2006-04-09
Yeah, you need new drivers. Try doing the following from the console.

> sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-glx-config enable

And if it doesnt work, "sudo dpkg-reconfigure xserver-xorg" is worth a shot (choose the "nvidia" driver, not the "nv")

---

### Post by slipk487 on 2006-04-09
ya run ```
sudo dpkg-reconfigure xserver-xorg
``` and u might need to know the id of the pci card if it cant auto detect it

---

### Post by djoefish on 2006-04-09
thanx...I'll try it

---

### Post by djoefish on 2006-04-09
It worked!! Thanks a lot.

---

