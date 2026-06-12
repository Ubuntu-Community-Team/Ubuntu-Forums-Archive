---
title: "Nvidia Drivers"
date: 2006-06-03
forum: General Help
---

### Post by frizzl on 2006-06-03
well after installing the 8762 drivers, my X server no longer works :(

it crashes before i get into the gui (except the loading bar shows) and says that the xorg.conf is not set up correctly. I am on 64 bit ubuntu.

---

### Post by givré on 2006-06-03
[QUOTE=frizzl]well after installing the 8762 drivers, my X server no longer works :(

it crashes before i get into the gui (except the loading bar shows) and says that the xorg.conf is not set up correctly. I am on 64 bit ubuntu.[/QUOTE]
How did you install your driver, did you see this guide [http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)
Also, can you put here your /etc/X11/xorg.conf

---

### Post by frizzl on 2006-06-03
[QUOTE=givré]How did you install your driver, did you see this guide [http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html](http://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html)
Also, can you put here your /etc/X11/xorg.conf[/QUOTE]

i pressed CTRL ALT F1, 'stopped' gdm

then installed the driver using sudo sh nvidia-install...etc

the installer says it will update X server for me, then... reboot, and X server is not configured properly

i cant post my xorg.conf as i cant access it to copy :(

---

### Post by tseliot on 2006-06-03
Try my guide, please:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

You can ask further questions there

---

### Post by givré on 2006-06-03
If you have a windows partation and if you don't really know how to access your xorg.conf, i recommand you explore2fs [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

This apps will permit you to view your linux partition, and so you will b able to post here your /etc/X11/xorg.conf
After doing that, you will probably have to configure it with the nv driver (we will help you ;) ), 
And when you will be able to run X, follow tseliot guide

---

