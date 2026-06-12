---
title: "Boot Screen is an underscore?"
date: 2010-06-15
forum: General Help
---

### Post by mp3c on 2010-06-15
Is there a more prettier boot screen than a blinking underscore (one of these _) on Ubuntu 10.04 LTS Desktop?

Just curious,
mp3c

---

### Post by cariboo on 2010-06-15
There are several plymouth themes, have a look [here]("http://www.webupd8.org/2010/01/look-at-ubuntu-lucid-plymouth-themes.html"), a lot depends on your graphics adapter and what drivers you are using. Plymouth works the way it should on my netbook with i945 graphics, while on two systems with nvidia graphics cards (GT210 & 9400GT) the image is a bit large. It's easy enough to fix, I just haven't got around to it yet. :)

---

### Post by anglican on 2010-06-16
> **mp3c said:**
> Is there a more prettier boot screen than a blinking underscore (one of these _) on Ubuntu 10.04 LTS Desktop?

Just curious,
mp3c
Does the following help?
```
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
``````
sudo update-initramfs -u
```H

---

### Post by jondodson on 2010-06-23
Well, I'm not the OP, but I came here for the same reason - an ugly & texty boot with the splash screen only finally appearing about two seconds b4 the desktop comes up.  Texty close down too.

Executing these two commands fixed it.  Thanks anglican!

---

