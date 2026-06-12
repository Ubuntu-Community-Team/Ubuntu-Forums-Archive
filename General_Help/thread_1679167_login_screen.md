---
title: "login screen"
date: 2011-01-31
forum: General Help
---

### Post by widggman on 2011-01-31
Hi,

  So a few days ago, I upgraded my driver for my videocard... and since then, when I reboot my computer, I have to login in console mode, instead of the normal one.

  I reinstall the previous driver that I have... but finally, the same problem happens.

  I checked the settings for the login screen... and my setting is: Ubuntu Desktop Edition.

  So, there's a file somewhere, that was affected by the installation. And now, each time I log in, I have to stop gdm... just start the installation of the driver (don't even have to do it completely... just stop when they says it's the same version of the driver) then restart gdm.

  I don't want to do that anymore... it's long... it's a wast of time. So, which file do I have to change ? Where is that bug coming from ?

  Someone here knows how to solve this.

  Thanks

W

---

### Post by davidmohammed on 2011-01-31
go on - give us a hint... what is your graphics card (lspci | grep VGA), how did you install the driver (what instructions)?

---

### Post by widggman on 2011-01-31
nVidia GeForce 9800 GTX+

I installed the driver 260.19.36

For the driver, I installed it like I installed all the previous version of the driver.
- stop gdm
- sudo sh <driver_file>.run
- follow the instruction on the screen
- start gdm

---

### Post by davidmohammed on 2011-01-31
suggest first clean up your nvidia installation

from memory the syntax is something like

sudo apt-get --purge remove nvidia*

or

sudo apt-get purge nvidia*

does this help with your boot problems?

---

### Post by widggman on 2011-01-31
i will try this and let you know if it works!

---

### Post by bodyeuh on 2011-01-31
try this: 

1] boot ubuntu in recovery mode 

2]Change to the x11 directory. Delete the xorg.conf cd /etc/X11 sudo rm xorg.conf also remove all xorg.conf files
  3] reboot PC after all xorg.conf are removed and let Ubuntu restart. Re-enable Restricted Drivers
  4] Go to terminal. Type sudo nvidia-settings. Select the correct video settings for your display. 
source: [http://superuser.com/questions/63586/ubuntu-fails-to-start-xorg-after-upgrade-to-9-10](http://superuser.com/questions/63586/ubuntu-fails-to-start-xorg-after-upgrade-to-9-10)

---

### Post by widggman on 2011-01-31
Hehe,

  I actually did both solutions. One alone was not enough... but hey, it worked.

  I also noticed that when I purged nvidia, it uninstall pyopencl... which was the reason why I had to upgrade my driver. So it might have cause something weird when I installed it... or a package that it uses (probably with the name nvidia in it) was probably interfering with the nVIDIA driver.

  Thanks again for the help

W

---

