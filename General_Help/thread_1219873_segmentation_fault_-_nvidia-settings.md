---
title: "segmentation fault - nvidia-settings"
date: 2009-07-22
forum: General Help
---

### Post by pcgstudio on 2009-07-22
I try to run nvidia-settngs and it gives me segmentation fault

when i try to load it via the system menu it wont load either

i need to be able to load it, dont know why it is not loading

---

### Post by pcgstudio on 2009-07-22
i reinstalled the drivers and still nothing :S at one point it ran but said the xconfiguration file was not installed or something so i did nvidia-xconfig, and after that it wouldnt work again

---

### Post by pcgstudio on 2009-07-22
i know i might be being impatient but help please, i cant use my twin view without nvidia settings working

---

### Post by jimmyhacker on 2009-07-22
such a crap.this is why i leaved ubuntu.Cannonical launchs unstable .debs.

---

### Post by fooman on 2009-07-22
> **pcgstudio said:**
> i reinstalled the drivers and still nothing :S at one point it ran but said the xconfiguration file was not installed or something so i did nvidia-xconfig, and after that it wouldnt work again

did you try "*sudo* nvidia-xconfig"?  then log out and back in again (or just reboot).

---

### Post by pcgstudio on 2009-07-23
yeap that was the first thing i did, replaced the xorg.conf and restarted gdm

---

### Post by ibuclaw on 2009-07-23
> **pcgstudio said:**
> yeap that was the first thing i did, replaced the xorg.conf and restarted gdm

Could you give us any hints about your system?

Ubuntu Version? 32bit? 64bit?

```
dpkg -S $(which nvidia-settings) | cut -f1 -d: | xargs apt-cache show
```

Regards
Iain

---

### Post by pcgstudio on 2009-07-24
sorry its ubuntu version jaunty with 32bit but i do have a 64bit processor. running nvidia 7600gt i used envy to install the driver. 

```
Package: nvidia-settings
Priority: optional
Section: x11
Installed-Size: 1888
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Debian NVIDIA Maintainers <pkg-nvidia-devel@lists.alioth.debian.org>
Architecture: i386
Version: 180.25-0ubuntu1
Replaces: libxnvctrl-dev
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.15.0), libpango1.0-0 (>= 1.22.0), libx11-6, libxext6, zlib1g (>= 1:1.1.4)
Conflicts: libxnvctrl-dev
Filename: pool/main/n/nvidia-settings/nvidia-settings_180.25-0ubuntu1_i386.deb
Size: 771986
MD5sum: acab1c19db929cec6981f0ad3b8bebda
SHA1: fa5d4aa6d437d14535cbdc1aa8bd7022953b57c7
SHA256: 6cb5f59c71531c1a3b52e198917a0aa8607efbd1447932b96d13b7ff6710026e
Description: Tool of configuring the NVIDIA graphics driver
 The nvidia-settings utility is a tool for configuring the NVIDIA
 Linux graphics driver.  It operates by communicating with the NVIDIA
 X driver, querying and updating state as appropriate.  This
 communication is done with the NV-CONTROL X extension.
 .
 Values such as brightness and gamma, XVideo attributes, temperature,
 and OpenGL settings can be queried and configured via nvidia-settings.
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

Package: nvidia-settings
Priority: optional
Section: contrib/x11
Installed-Size: 1776
Maintainer: Randall Donald <rdonald@debian.org>
Architecture: i386
Version: 1.0+20060516-3
Depends: libatk1.0-0 (>= 1.12.2), libc6 (>= 2.3.6-6), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.4.0), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.14.7), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxrandr2, libxrender1
Recommends: nvidia-glx (>= 1.0.6106)
Filename: pool/contrib/n/nvidia-settings/nvidia-settings_1.0+20060516-3_i386.deb
Size: 760798
MD5sum: 1333689a9839e7205f0bc0406186808f
SHA1: c2d036105bbf00117db0b4f16e1dc160de971fbf
SHA256: 2c6aad767e1c70d5085e7771c60da79bed9fcb204dba65f1b2702044154e5971
Description: Tool of configuring the NVIDIA graphics driver
 The nvidia-settings utility is a tool for configuring the NVIDIA
 Linux graphics driver.  It operates by communicating with the NVIDIA
 X driver, querying and updating state as appropriate.  This
 communication is done with the NV-CONTROL X extension.
 .
 Values such as brightness and gamma, XVideo attributes, temperature,
 and OpenGL settings can be queried and configured via nvidia-settings.
Tag: uitoolkit::gtk

```

---

