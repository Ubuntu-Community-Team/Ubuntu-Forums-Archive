---
title: "graphical issues on startup"
date: 2010-11-30
forum: General Help
---

### Post by jtkiv on 2010-11-30
using ubuntu 10.10, also happened with 10.04.

on startup, maybe 50% of the time i get major display problems.  screen  is either mostly black or a strange striped pattern that is mostly white  with blue red and green speckles :wink:

i included a screenshot i managed to save without seeing what i was doing.

anyhow, a restart generally takes care of it, right now im posting from  the same computer and everything looks fine.  i dont seem to have any  performance issues other than a minor bug in spring rts, which now that i  think about it, could be related.  basically it freezes for ~10  seconds, no display settings seem to affect it.

not sure what the cause is... anyone have any ideas?

Ubuntu 10.10, AMD Athlon 3200+, nVidia geForce FX5500

---

### Post by sikander3786 on 2010-11-30
The problem might be your graphics card.

Did you install any proprietary drivers for that? I think they are not available in 10.10....?

Is there a custom xorg.conf? If yes what does that contain?

```
cat /etc/X11/xorg.conf
```

---

### Post by jtkiv on 2010-11-30
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


and i am using a propriety driver, "NVIDIA accelerated graphics driver (version 173)"  i prefroms much better than the open source drivers.

so if it is the graphics card, why would it happen only on start-up and be inconsistent at that?

---

### Post by sikander3786 on 2010-11-30
How did you manage to install Nvidia 173 on Ubuntu 10.10? I think it is not available for Maverick.

Anyhow I would recommend to just remove your xorg.conf and reconfigure your Graphics and let X directly deal with all the display stuff.

Backup your existing xorg,conf by,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Delete the original,

```
sudo rm /etc/X11/xorg.conf
```

Reconfigure your graphics,

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot a couple of times and see if that still happens.

---

### Post by jtkiv on 2010-12-02
appears to take care of it, but graphics become terribly slow without that config file.  spring wont launch because the resolution isnt listed...  

seems like a pick between evils and the startup issues are more favorable than sluggish performance.

any way to have the best of both worlds?  can i modify something in that file?  add something?  why does it make that big of a difference in rendering speed?

thanks for the help.

---

### Post by sikander3786 on 2010-12-02
You can regenrate that file by,

```
sudo nvidia-xconfig
```

Did you check under System > Administraion > Nvidia X Server Settings? Does it list any acceptable resolution?

---

### Post by jtkiv on 2010-12-06
after a couple days, here's what i found:


removing xorg.conf, but still using nVidia 173 driver results in very slow graphics, but successful start ups.

removing xorg.conf, and removing nVidia 173 driver results in acceptable graphic speeds, and successful startups.

keeping xorg.conf and nVidia 173 results in the best graphic speed but usually requires 3-4 restarts before it works.


so for now im sticking with #2.  thanks for the help.

---

