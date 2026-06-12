---
title: "Anybody know how to edit xorg.conf from recovery terminal?"
date: 2009-11-12
forum: General Help
---

### Post by gabdullah on 2009-11-12
I was trying to tweak my laptop's trackpad settings in xorg.conf and I screwed something up. Now, when I boot, I can get to the grub menu, select Ubuntu, and then it screws up the graphics display when I get to the login page (the screen doesn't load, and I end up with lines at the top of the screen, while I can make out the login page in the background). 
On my windoze partition, everything works fine, so I know the hardware is fine. 
Any ideas?

---

### Post by billyboy1978 on 2009-11-12
$ sudo nano /etc/X11/xorg.conf

---

### Post by aminesoft on 2009-11-12
> **billyboy1978 said:**
> $ sudo nano /etc/x11/xorg.conf
+1

---

### Post by gabdullah on 2009-11-12
Fixed!
Here's what I did...
Followed the above advice to check the file, then rebooted, went into recovery mode, selected the command line with networking, and:
sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg

Back in ubuntu. Peace out, vista.

---

