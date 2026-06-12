---
title: "Xorg.conf has barely any data?"
date: 2011-11-24
forum: General Help
---

### Post by Bryan334 on 2011-11-24
I reinstalled Ubuntu, I installed my drivers, and then I went to check my Xorg.conf file and this is all it has...
[PHP]
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
 [/PHP]

---

### Post by Dejavou42 on 2011-11-24
Is there a problem? If everything works, just leave it alone. If you are having problems try to run:

```
sudo X -configure
```

it will put an xorg.conf.new in your home folder. backup your old xorg.conf and replace it with xorg.conf.new.

---

### Post by ptrakk on 2011-11-24
if you dont specify anything in that file it will do it all in the hardware abstract (HAL) layer. i think you could do something like  dpkg-reconfigure xserver-xorg or something.

---

### Post by grahammechanical on 2011-11-24
I think that the X-server gets its monitor settings from the monitor through the video card as it loads. I do not think that it reads a script. Otherwise we would need to set the screen resolution ourselves when we install and when we change monitors.

I base this view on the problems I had due to an overheating video card that put me into low resolution mode at boot time. It eventually messed up the video settings completely and I could not even run a live CD to re-install. For this reason I think that the live CD will take settings from a pre-existing Ubuntu install.

I was able to install a 2007 Mandrivia OS where I set the resolution during the install process. Which is something that I have never had to do in Ubuntu.

As a previous post said: If it ain't broke, don't fix it.

Regards.

---

