---
title: "Ubuntu And Raspberry Pi"
date: 2012-04-30
forum: General Help
---

### Post by carmenin87 on 2012-04-30
In the reading that I have done, I can't seem to find if the ultra-cheap Raspberry Pi supports Ubuntu Linux or not.

Would anyone know?

Thank you

---

### Post by RexFuzzle on 2012-04-30
As far as I know it doesn't until somebody build it, which I haven't seen yet.

---

### Post by holycow131415 on 2012-04-30
[http://www.raspberrypi.org/downloads](http://www.raspberrypi.org/downloads)

They are the only supported. if i was you, id use debian

---

### Post by 3rdalbum on 2012-04-30
Ubuntu does not support the particular ARM CPU that the Raspberry Pi uses, so the next best thing is to install Debian on the Pi.

---

### Post by SteveDee on 2012-06-01
> **3rdalbum said:**
> ...so the next best thing is to install Debian on the Pi.

The recommended Debian distro for RPi runs with LXDE, so Lubuntu users will feel at home.

When set to Auto boot into LXDE, it boots to the desktop in just 30 seconds. It will support many of the 'buntu/Debian applications available as deb packages, and special builds for apps like Gambas have already appeared.

Browsing the web is a bit slow on the RPi, and playing videos is not great unless you have a hardware-accelerated video player. But its a great project card.

---

### Post by Cheesemill on 2012-06-01
Ubuntu announced it was dropping support for ARM v6 (the version Raspberry Pi uses) in 2010 with the release of Lucid (10.04).

Ubuntu now only has an ARM port for v7 and higher processors so in other words no, Ubuntu won't be available for the Raspberry Pi.

As others have mentioned you should go with Debian instead as it uses the same package format and package management tools (.deb and apt-get) so you should feel right at home.

---

