---
title: "Problem with kernel and nvidia drivers."
date: 2009-08-05
forum: General Help
---

### Post by audriens on 2009-08-05
Hi,when my ubuntu loads then goes black screen, my all kernels crashed, i start ubuntu, choosing recovery mode, then choose "xfix try to auto repair graphic problem", when i want to change resolution i get message "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." I do wath it ask, but when i restart x server i get black screen. What should i do?

---

### Post by soapBAR2 on 2009-08-05
This could be any number of things.
1) Are you running a non-automagic'd GRUB menu.list (did you customise it yourself)? The nvidia driver is finnicky about using old kernels, and if you didn't update your menu.list when your kernel was upgraded, you're booting into your old kernel
2) Are you using the recommended driver for your chip (I'm going to assume you used a GUI to load the driver, which should recommend a driver to you).
3) The driver install may have just been borked somehow
4) Something else

Try this:

```
dpkg-reconfigure xserver-xorg
```

In your shell. That will reset your xorg.conf to default, and you'll be back in non-proprietary-driver mode (slow, but it works). Then, try installing the driver again using envy.

GNOME, XFCE (Ubuntu, Xubuntu):
```
sudo apt-get install envy-gtk
```

KDE (Kubuntu):
```
sudo apt-get install envy-qt
```

It doesn't particularly matter if you install the gnome version on kde or visa versa (a, but it'll look/work nicer if you pick the right one.

---

