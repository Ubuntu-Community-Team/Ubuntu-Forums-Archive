---
title: "Semi-Official MSI WInd U100 Workaround Thread"
date: 2010-10-01
forum: General Help
---

### Post by dh04000 on 2010-10-01
So, a new Ubuntu release, and many bugs for our little MSI Wind U100 netbooks. Mnay inherited from Lucid unfortunately.

There is what I've discovered so far:

[B]

Ubuntu shuts down after unplugging Laptop power cord
A problem known with MSI wind and some Vostro users.[/B]

Current workaround: is to open gconf-editor and browse to:
Code:

/apps/gnome-power-manager/general

And de-select the option use_time_for_policy

There is no need to restart, just close the configuration editor.


[B]
Other graphics card users including nVidia may get a black screen with flashing cursor and then a very short duration plymouth.[/B]

BUG Location: [https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)

Workaround: One fix for this is to create this file.
Code:

gksu gedit /etc/initramfs-tools/conf.d/splash

and add this option FRAMEBUFFER=y, save the file.
Then
Code:

sudo update-initramfs -u

---

