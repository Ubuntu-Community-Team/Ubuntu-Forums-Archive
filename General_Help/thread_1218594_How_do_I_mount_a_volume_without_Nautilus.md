---
title: "How do I mount a volume without Nautilus?"
date: 2009-07-20
forum: General Help
---

### Post by jgor on 2009-07-20
I have used Ubuntu for a while now and have found the default file manager to be embarrassingly slow. I have installed alternatives to Nautilus which are much faster. My favorite alternative so far is Gnome Commander but I can't figure out how to access an unmounted CD, jump drive, or partition with it. As of now if I want to access an unmounted volume with Commander I need to open it with nautilus first, which is sort of ridiculous. Is there a way for me to become independent of Nautilus (which I find is actually slower than Windows Vista's file manager) on Ubuntu?

---

### Post by blueridgedog on 2009-07-20
When you plug in a mountable external media, Linux/Ubuntu mounts it and you can access it with a variety of file managers.  When I plug in a USB flash drive, it is mounted and in Gnome Commander, it shows up on the top bar, just below the icons.

Check out the section on using removable devices with Gnome Commander on this site:

[http://www.nongnu.org/gcmd/tips.html](http://www.nongnu.org/gcmd/tips.html)

---

### Post by vegetarianshrimp on 2009-07-20
edit: achh sorry can't read "without"

---

### Post by michy99 on 2009-07-20
If it is an internal drive, you can mount it automatically at start-up by adding an entry in /etc/fstab. Usb devices should mount when you plug them in.

---

### Post by jgor on 2009-07-21
Thank you for your help.
This problem must only be on my computer. Technically I am using Linux Mint Elyssa not Ubuntu, I may have uninstalled the package responsible for displaying the desktop on the background, and I can live with Nautilus running in the background. I started this thread thinking that maybe this issue was on all ubunutu computers. But since it isn't it really isn't that important because come October I'll probably end up, as always, doing a clean installation of the next Ubuntu. However, Gnome Commander actually does not mount devices/volumes for me now. But never-mind this, it may just be because I used the wrong deb package to install Commander.

---

### Post by blueridgedog on 2009-07-21
Would you like some advice on mounting them manually and then navigating to the mounted location using Gnome Commander?

---

