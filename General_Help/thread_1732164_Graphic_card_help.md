---
title: "Graphic card help"
date: 2011-04-17
forum: General Help
---

### Post by GangusKhan on 2011-04-17
I dont know what graphics card i have and what driver i need for it because i have had had errors saying i need driver and in "additional driver" thing it says there are none? can someone tell me how to figure out what driver i need

---

### Post by pqwoerituytrueiwoq on 2011-04-17
run this command
```
lspci | grep VGA
```
and post what it gives you

---

### Post by GangusKhan on 2011-04-18
01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a3)

---

### Post by wolfen69 on 2011-04-18
> **GangusKhan said:**
> 01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a3)

If nothing shows up in additional drivers, that card may no longer be supported by default in ubuntu. You may have to install the drivers manually from nvidia. But after a quick check, I don't see any for that card. But the drivers for the geforce4 series may work.

---

### Post by GangusKhan on 2011-04-18
Yes, ok thanks I think I'm just going to buy a new card as soon as I can

---

### Post by ronnielsen1 on 2011-04-18
[http://www.nvidia.com/object/linux-display-ia32-71.86.14-driver.html](http://www.nvidia.com/object/linux-display-ia32-71.86.14-driver.html)

Ge force 4 takes a different driver than 2

Jockey isn't the best at detecting older nvidia cards.

If you click on the link above that should be the driver you need

[http://us.download.nvidia.com/XFree86/Linux-x86/71.86.14/README/README](http://us.download.nvidia.com/XFree86/Linux-x86/71.86.14/README/README)

You have to install the driver outside of X - The next link might help with that

[http://eddieringle.com/how-to-install-official-nvidia-drivers-in-linux/](http://eddieringle.com/how-to-install-official-nvidia-drivers-in-linux/)

---

### Post by pqwoerituytrueiwoq on 2011-04-18
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

sudo service gdm stop # write down or remember the following
Alt+F1
#Login to the tty
sudo sh /home/$USER/Downloads/NVIDIA-Linux-[HIT TAB  KEY]
#go through the install process
sudo service gdm start

**you will have to do this after every kernel upgrade**

---

### Post by Nutria on 2011-04-18
> **GangusKhan said:**
> 01:00.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a3)

This is a *really* old card.  I'm not surprised that nouveau doesn't support it.  Not even nvidia driver v96.43.19 supports it...

---

