---
title: "Gradual performance degradation in Lucid"
date: 2010-05-04
forum: General Help
---

### Post by ProphetOfDoom on 2010-05-04
So I'm posting this mostly in case it helps others, but if you found a different fix for this problem let me know.

Problem: 
Upgraded from karmic to Lucid. Everything appeared well but I've noticed a gradual performance degradation in X performance particularly with Gimp/wacom tablet which I use a lot. After about 30 minutes the wacom is so laggy as to be virtually useless. Not such an obvious problem with other apps like firefox.

I don't think this is the same issue as the well publicized X memory leak issue that plagued earlier candidate releases of Lucid.

I'm using an ATI RV280 (9200SE) graphics card. I'm sure the issue is KMS that is set to on by default in this release.

Solution
Switch KMS off (revert to UMS) and install the libgl1-mesa-glx and libgl1-mesa-dri packages from jaunty (newer packages are all broken - you'll get a black background problem if you use anything newer - at least with the RV280 graphics card).

First, switch off KMS:
sudo echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf

then locate and install the older packages from jaunty:
sudo dpkg --install libgl1-mesa-glx_7.4-0ubuntu3.3_i386.deb
sudo dpkg --install libgl1-mesa-dri_7.4-0ubuntu3.3_i386.deb

Reboot

Shame I have to use one year old packages but at least it now works. :)

---

