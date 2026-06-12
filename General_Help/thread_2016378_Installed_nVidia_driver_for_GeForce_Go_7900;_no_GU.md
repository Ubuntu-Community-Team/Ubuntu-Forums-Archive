---
title: "Installed nVidia driver for GeForce Go 7900; no GUI"
date: 2012-07-04
forum: General Help
---

### Post by u-noob-tu on 2012-07-04
I manually installed nVidia driver 295.59 on a Dell Inspiron E1705 with a GeForce Go 7900 GS. Now i have no GUI, just a full screen terminal. Ive tried removing the driver and it works again, but the screen is only at a resolution of 1280x1024 when it should be 1920x1080. Not sure how to fix this. Any ideas?

---

### Post by dino99 on 2012-07-04
maybe it conflict with a borked xorg.conf

sudo rm /etc/X11/xorg.conf

sudo apt-get purge nvidia-current
sudo apt-get install nvidia-current

sudo jockey-gtk
(to check driver activation)

logout/in

---

