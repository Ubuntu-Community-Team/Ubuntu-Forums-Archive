---
title: "Why install 'libgtk2.0-dev' force me to remove 'libgli-mesa-dev:i386'?"
date: 2012-05-30
forum: General Help
---

### Post by mjsilverstri on 2012-05-30
Why when I install 'libgtk2.0-dev' forces me to remove  'libgli-mesa-dev:i386'?

I need  'libgli-mesa-dev:i386' to compile 1 project and I need  'libgtk2.0-dev'for another.

> $ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-common-dev:i386 libdrm-dev:i386 libkms1:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libxcomposite-dev libxext-dev libxi-dev libxinerama-dev libxrandr-dev
Suggested packages:
  libgtk2.0-doc
The following packages will be REMOVED:
  libgl1-mesa-dev:i386 libxext-dev:i386
The following NEW packages will be installed:
  libgtk2.0-dev libxcomposite-dev libxext-dev libxi-dev libxinerama-dev
  libxrandr-dev
0 upgraded, 6 newly installed, 2 to remove and 58 not upgraded.
Need to get 24.9 kB/4,262 kB of archives.
After this operation, 20.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

How can I fix it?

Thank you.

---

