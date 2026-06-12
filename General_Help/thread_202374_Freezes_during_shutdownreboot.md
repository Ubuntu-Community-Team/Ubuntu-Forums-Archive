---
title: "Freezes during shutdown/reboot"
date: 2006-06-23
forum: General Help
---

### Post by STVA on 2006-06-23
I have a new 6.06 install, everything works great, but every time I reboot or shutdown my computer hangs before it even exits X.  I am using the proprietary ATI driver, but besides that everything is standard.  This is on a compaq PC.  More info can be provided.  Thanks

---

### Post by x64Jimbo on 2006-06-23
Known bug:
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/30447)
It's being worked on - I'm in the same boat as you.
If you want to get it working so it will reboot & shutdown properly, you could try booting from Ubuntu LiveCD and capture the xorg.conf file that it generates, and replace your current one with that. The xorg.conf file that the LiveCD generates usually doesn't include anything for the 3D acceleration, so you should be safe.

---

### Post by STVA on 2006-06-23
Thank you sir you are a gentlemen and a scholar.

---

