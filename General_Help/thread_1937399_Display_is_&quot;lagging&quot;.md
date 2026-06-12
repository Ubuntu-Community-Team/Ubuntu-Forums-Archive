---
title: "Display is &quot;lagging&quot;"
date: 2012-03-07
forum: General Help
---

### Post by dbbolton on 2012-03-07
I'm running Ubuntu 11.10 amd64 and I have an Nvidia Geforce Go 7300 with the 295.20 version of the proprietary driver installed.

Quite often, my display seems to "lag". That is the best way I can describe it. For example, I might delete some text in a document in LibreOffice but the text will stay on the screen for a few seconds.

However, this is not an application issue. I have noticed the same behavior in evince and Firefox as well. In firefox, it is especially bad when I scroll down on a webpage with the mouse (smooth scrolling is off, by the way). There are artifacts everywhere.

What could be causing this?

```
$ uname -r
3.0.0-15-generic
$ cat /etc/issue
Ubuntu 11.10 \n \l

$ lspci | grep V
01:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
$ nvidia-installer --version

nvidia-installer:  version 295.20 
(buildmeister@swio-display-x86-rhel47-05.nvidia.com)  Mon Feb  6 22:13:45 PST
2012
  The NVIDIA Software Installer for Unix/Linux.

  This program is used to install, upgrade and uninstall The NVIDIA Accelerated
  Graphics Driver Set for Linux-x86_64.

  Copyright (C) 2003 - 2010 NVIDIA Corporation.

$ 

```

---

