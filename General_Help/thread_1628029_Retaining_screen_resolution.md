---
title: "Retaining screen resolution"
date: 2010-11-22
forum: General Help
---

### Post by John Franklin on 2010-11-22
Every time Ubuntu (10.04) starts, it uses a screen resolution of 1024x768. I change this successfully through Preferences to 1280x1024, but it is never remembered at the next boot. How do I ensure that it is.

(I've read that an etc/X11/xorg.conf file may be used for this, but I don't have one and am unsure what I need to put into one)

---

### Post by TeoBigusGeekus on 2010-11-22
What is your graphics card?
If you use nvidia, you should launch the nvidia utility by
```
gksu nvidia-settings
```
make changes and then press the save to x configuration in order to make the changes permanent.

---

### Post by John Franklin on 2010-11-22
My card is nvidia but nothing happens when I run gksu nvidia-settings (presumably the utility is not installed)

---

### Post by Grenage on 2010-11-22
```
sudo apt-get install nvidia-settings
```

---

