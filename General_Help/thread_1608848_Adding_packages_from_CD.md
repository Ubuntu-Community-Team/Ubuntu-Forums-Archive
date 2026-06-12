---
title: "Adding packages from CD"
date: 2010-10-29
forum: General Help
---

### Post by darkcoffee on 2010-10-29
Barebone install. No connection.

How do I add packages from the Ubuntu desktop CD?

sudo apt-cdrom add
sudo update

/etc/apt/source.list confirms that the CD repo has been added.

Tried to "sudo xserver-xorg-video-sis" but got a "E: Unable to locate package."

Please help.

---

### Post by diesch on 2010-10-29
You can't use the Desktop CD  to install üpackages , that only works with the alternate CD. 

As the Desktop CD is used as a Live CD it doesn't contain package files but installed software.

---

