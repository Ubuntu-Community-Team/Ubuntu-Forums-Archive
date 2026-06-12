---
title: "Can't bootup after fresh install: no screens detected"
date: 2011-06-10
forum: General Help
---

### Post by Pithikos on 2011-06-10
I am a bit puzzled about this. At first I tried to install Ubuntu 11.04 but after I enabled my second monitor through nVidia settings I couldn't boot. At that point I didn't know the problem had to do with that. I tried to reinstall Ubuntu but the install hanged so I downloaded and tried Mint thinking that the CD was defect.

Now after enabling the second monitor via nVidia Settings I can't boot still. Bootup stalls at "Checkingg battery". I can press CTRL+ALT+F1 to open a shell. If I type "startx" then I get this:

```
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) No devices detected.

Fatal server error:
no screens found
```

I tryied "dpkg-reconfigure xserver-xorg" but that didn't help much.

My graphic card is G92 Geforce 8800GT. Driver used is 173.14.30
I run on Mint 11 64x

I attach my xorg.conf and log file.

---

### Post by Pithikos on 2011-06-10
Removing the xorg.conf seems to fix this. But I want to use my second monitor :(

---

