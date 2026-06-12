---
title: "Monitor out of range with Ubuntu 10.04"
date: 2010-06-17
forum: General Help
---

### Post by GeoMX on 2010-06-17
I have and old CRT monitor I'd like to use with my system, I've installed the latest Ubuntu version, when booting, I can see the plymouth screen but, after that, the monitor goes black and shows a "out of range" message. but If I switch to a virtual terminal (Ctrl+Alt+F1), the monitor works.

Also, If I unplug the monitor and start/reboot the system, and later plug it, I have video on the screen! I can see GDM and log into the system. So I guess the problem is that Ubuntu sets a wrong mode for my monitor, what I don't understand is why it works if I plug it in after the system has started :confused:.

I've tried setting grub resolution to 640x480 and 800x600, then using "nomodeset" as parameter in GRUB_CMDLINE_LINUX, but can't get it working when the monitor is plugged when starting the system.

Thanks in advance for any help/comment/suggestion.

----------------------
I solved it by creating a xorg.conf file, I had read recent kernel versions should work without it, but can be used for situations like this.

It works now :).

---

