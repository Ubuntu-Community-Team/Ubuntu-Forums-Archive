---
title: "Proprietary nvidia drivers = ugly bootup"
date: 2010-09-26
forum: General Help
---

### Post by eveningsky339 on 2010-09-26
I'm using an Nvidia Geforce 6x card (can't remember the exact number).  When I do not have the proprietary driver enabled, the Ubuntu logo and status bar, as well as various boot up messages, look very nice.  They are scaled properly and I'm impressed with how they look.

When I do enable the proprietary driver, the screen resolution during boot up is much smaller, and therefore everything looks ugly.  The little status bar under the Ubuntu logo suddenly fills up and "freezes."  The transition from login screen to desktop is jerky.

Unfortunately if I disable my card, I cannot use desktop effects or even view flash videos in full screen mode.  (I'm assuming nouveau still has work to do.)

Is there any way I can have proprietary drivers enabled *and* a nice boot up experience?

---

### Post by ellgor on 2010-09-27
Hi,

I read that the nvidia drivers dont get istalled correctly, for some reason, causing irregularities, I found this guide that gets them installed and running correctly:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"

Note: If you get an error message like this "Unable to find kernel source tree", do this:
$ sudo apt-get install linux-headers -`uname -r'

then ran the installer again

8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

You can change the login-screen from "admin-login-screen" change the resolution and colour(24bit) to get a better screen.

---

### Post by psycho5 on 2010-09-27
Or if you want to stick with ubuntu's drivers and still have a good bootup, you can use this guide:

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

It works with my nvidia and it works with 10.10 also.

---

