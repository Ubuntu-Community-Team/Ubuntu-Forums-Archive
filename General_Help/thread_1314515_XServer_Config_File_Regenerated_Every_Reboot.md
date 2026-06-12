---
title: "XServer Config File Regenerated Every Reboot"
date: 2009-11-04
forum: General Help
---

### Post by digiPixel on 2009-11-04
Recently Ubuntu had trouble booting up with the failsafe window popping up (xserver failed to start). I use a custom xorg.conf file since Ubuntu's autodetection for the monitor and graphics card settings fails because of the monitor that is used. The monitor is a SlimAGE LCD which does not have the handy recalibrate button (an early version LCD monitor).

Ubuntu's autodetection with this monitor fails to pick up the 1024x768 resolution and does not properly pick up the specific refresh rates, since the monitors display is positioned by the refresh rate. If an incorrect refresh rate is used then either the whole display cannot be seen, or the monitor displays a blue screen saying the mode is incorrect. To make matters worse if a different graphics driver is used by xserver then different refresh rates have to be supplied that the monitor will recognize, so it can be a bit of a guessing game and Russian roulette (what a headache!).

After inspecting the xorg.conf file I discovered that something has completely regenerated it. Any changes made to that file are ignored since xserver has been directed to use xorg.conf.failsafe instead. I do not know how to direct xserver to permanently use xorg.conf. Even worse is the fact that xorg.conf.failsafe (the primary xserver config file) is regenerated every reboot, thus any changes made to the file are lost.

I have tried to reinstall the Ubuntu xorg packages but to no avail. It is not known what is causing the problem. Currently it looks as though a clean reinstall of Ubuntu is needed.

I am extremely reluctant to upgrade to a newer version of Ubuntu since it does away with the xorg.conf file completely. Since Ubuntu's autodetection is very poor I do not have much confidence that newer versions of Ubuntu will do any better. It would be great if a tool could be found that can output the monitors settings (ones that work) based on the graphics driver that is used in xserver (eg the nvidia one not the nv one).

Here is the PC's configuration:

[LIST]
[*]Ubuntu Desktop 8.04 (32 bit)
[*]AMD Athlon64 2800+ CPU
[*]1GB DDR RAM
[*]Asus K8N motherboard
[*]Nvidia (ver 173.14.12) xserver driver
[*]SlimAGE LCD 1024x768 (24 bit) monitor (model not known)
[*]EnvyNG (ver 1.1.1) graphics driver tool- provides much better autodetection than Ubuntu's for ATI and NVidia video cards only
[*]Sysinfo (ver 0.7) tool
[*]LeadTek NVidia GeForce 7300GS AGP video card
[*]Edimax EW-7108PCg (RaLink RT2561/RT61 chipset) PCI wireless card
[/LIST]

---

### Post by grandtoubab on 2009-11-04
I upgrade from 09.04 to 09.10 since Alpha4 and my xorg files remains in /etc/X11 and never disappear


```
desktop:/etc/X11$ ls -alrt
total 120
-rw-r--r--   1 root root    13 2007-07-24 11:59 XvMCConfig
-rw-r--r--   1 root root   265 2008-05-14 02:10 Xsession.options
-rwxr-xr-x   1 root root  3730 2008-05-14 02:10 Xsession
-rw-r--r--   1 root root 17394 2008-05-14 02:10 rgb.txt
drwxr-xr-x   6 root root  4096 2008-07-02 12:21 fonts
-rw-r--r--   1 root root    14 2008-07-02 12:29 default-display-manager
drwxr-xr-x   2 root root  4096 2008-07-02 12:32 cursors
lrwxrwxrwx   1 root root    13 2008-10-17 22:10 X -> /usr/bin/Xorg
-rw-r--r--   1 root root  1253 2008-10-30 20:35 xorg.conf.dist-upgrade-200810302035
-rw-r--r--   1 root root  1441 2009-04-24 18:16 xorg.conf.dist-upgrade-200904241816
-rw-r--r--   1 root root  1439 2009-04-24 21:25 xorg.conf.20090424212552
-rw-r--r--   1 root root  1496 2009-05-18 15:27 xorg.conf.20090518152739
-rw-r--r--   1 root root   894 2009-05-18 15:28 xorg.conf.failsafe
-rw-------   1 root root   601 2009-08-26 19:44 Xwrapper.config
drwxr-xr-x   3 root root  4096 2009-08-26 20:02 xinit
-rw-r--r--   1 root root  1037 2009-08-26 20:20 xorg.conf.dist-upgrade-200908262020
-rw-r--r--   1 root root  1496 2009-09-20 10:34 xorg.conf.save
-rw-r--r--   1 root root  1499 2009-09-21 20:51 xorg.conf~
-rw-r--r--   1 root root  1524 2009-09-21 21:29 xorg.conf
drwxr-xr-x   2 root root  4096 2009-10-10 18:32 app-defaults
drwxr-xr-x   2 root root  4096 2009-10-15 17:31 xkb
drwxr-xr-x   2 root root  4096 2009-10-20 16:44 Xresources
drwxr-xr-x   9 root root  4096 2009-10-20 16:44 .
drwxr-xr-x   2 root root  4096 2009-10-26 17:32 Xsession.d
drwxr-xr-x 160 root root 12288 2009-11-04 19:45 ..
```

---

### Post by digiPixel on 2009-11-04
The xorg.conf file is still present, but it is the contents of xorg.conf.failsafe that keep on getting regenerated every reboot. No xserver configuration file disappears in /etc/X11.

---

