---
title: "Fixing x server"
date: 2009-08-13
forum: General Help
---

### Post by stareye on 2009-08-13
Well, I did something kind of stupid - I was trying to install the NVIDIA driver and was only able to get into text only mode in run level 1. Even though I was warned by the installer, I went ahead and lo and behold, X is broken. I then thought that since I was in run level 3 (since x is not working it is of course text based mode at this point) that if I tried the installer again it would work. Wrong. So, I then tried dpkg-reconfigure xserver-xorg and dpkg-reconfigure phigh xserver-xorg both to no avail. I tried to upgrade the xserver through apt-get but that did not work, and I am not sure if the backup of the original x configuration still exists (because I tried the installer twice). If it does, where do I find it and how do I restore it? And in case that does not work, what are other ways of restoring X? I am in edubuntu, if that makes any difference (still not sure how that happened, booted up the computer one day and bam, edubuntu logo there). It is also version 7.04. Any help is greatly appreciated, thanks!

---

### Post by P4man on 2009-08-14
try editing your xorg.conf and replace "driver NVIDIA" to "driver vesa" ?

---

### Post by stareye on 2009-08-14
Excellent, I reran dpkg-configure xserver-xorg and selected vesa instead of nvidia. Now X is working, but my usb mouse isn't :(. Must have set something incorrectly in the configuration. Thanks so much for the help!

---

