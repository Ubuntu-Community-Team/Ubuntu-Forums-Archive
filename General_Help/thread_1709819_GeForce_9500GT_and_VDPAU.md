---
title: "GeForce 9500GT and VDPAU"
date: 2011-03-18
forum: General Help
---

### Post by unbuntunewb on 2011-03-18
Hello,

I am having an extremely difficult time installing my new card. Its a Zotac Geforce 9500 GT. I want to be able to use it with VDPAU. I thought I had it installed but every time I turn on my computer it starts in low graphics mode. I have blacklisted  Nouveau and did the following:

ctrl alt f1
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-260.19.44.run
sudo /etc/init.d/gdm start

all appears well, it said it installed the drivers but it clearly did not. 

I have been at this for four hours I feel like tossing my computer into a puddle. Can someone please help me? This is my first ever hardware upgrade attempt with a Linux box. 

Thank you.

---

### Post by aktiwers on 2011-03-18
You need to reboot before the drivers can be used.

Have you tried uninstalling your current driver and then running the installer?

usually I install it like this:
```

sudo /etc/init.d/gdm stop
sudo chmod +x NVIDIA-Linux-x86-260.19.44.run
sudo ./NVIDIA-Linux-x86-260.19.44.run
sudo reboot

```

Edit: And remember to say "yes" when the installer wants to reconfigure your x settings

---

### Post by SeijiSensei on 2011-03-18
I've always had no problem installing the proprietary NVIDIA driver using the "Additional Drivers" (formerly "Hardware Drivers") applet that's in the standard menus.  I have an XTX 9500 which runs VDPAU just fine using smplayer.

I see many threads like this one that discuss problems with installing the drivers when downloaded from NVIDIA.  Since Ubuntu makes it so convenient to install the drivers using the applet, I've never bothered with the drivers on NVIDIA's site.

---

### Post by unbuntunewb on 2011-03-19
> **aktiwers said:**
> remember to say "yes" when the installer wants to reconfigure your x settings

I have done this but unfortunately it did not work

---

### Post by aktiwers on 2011-03-19
Have you tried:
```
sudo dpkg-reconfigure xserver-xorg
```

---

