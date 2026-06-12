---
title: "Which Nvidia driver to use?"
date: 2006-06-30
forum: General Help
---

### Post by erik-the-red on 2006-06-30
Since my computer was made in 2000, the card is a Nvidia TNT 2 Model 64. I checked synaptic and "xserver-xorg-driver-nv" was selected upon installation.

However, what about the package nvidia-glx-legacy? Will this improve performance or not?

---

### Post by Dr. Nick on 2006-06-30
yes the nvidia-glx-legacy will enable 3d acceleration on the card. So you can do more opengl stuff. If all you do is browse internet, email etc it wnt be a huge impact though. But if you do anything else like opengl games or screen savers i would install it

---

### Post by erik-the-red on 2006-07-01
Dr. Nick,

The reason why I asked is because the GL screensavers seem to be a big 'sluggish.' I recognize that my video card is very old, but I still feel that it should be able to handle the screensavers more smoothly than at present.

All I have to do is mark it for installation in Synaptic, right?

---

### Post by Dr. Nick on 2006-07-01
yeah, just install it in synaptic and check to make sure that your

/etc/X11/xorg.conf file list the driver as "nvidia" not "nv", If you look at the description in synaptic it will tell you a command you can run to enable the driver, this works sometimes, sometimes not. So just mark it for install then try to run the command it says, if you get a error just go
 **gksudo gedit /etc/X11/xorg.conf** from a terminal and change it yourself. That should speed up the screensaver some.

---

### Post by erik-the-red on 2006-07-01
Wow, the difference is incomparable. The screensavers used to visibly "shake." Now, they are much, much smoother.

Thanks!

---

