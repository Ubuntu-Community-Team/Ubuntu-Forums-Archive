---
title: "Wireless Support RT2500 Series"
date: 2011-05-13
forum: General Help
---

### Post by michaeldz on 2011-05-13
Hi.

I've been doing some research on how to update the drivers on my RT2500 chipset adapter. I have an Giada N3 mini-PC. Now Wireless works great right of the box using the GNOME Network manager. Nothing really to report, however, on my network there isn't a problem. On another network with a NETGEAR Wall-Plug Router, there is! 

It seems to work for a day, then, it tries to connect and....... eventually disconnects.

I've read a few tutorials on how to compile, install, these RT2500 drivers from source. Some people say it's the best chipset for Ubuntu. Also I've read another one using ndiswrappers. 

First, I want to be able to get rid of the old driver. So I delete /etc/network/interfaces file, and, I tried modprobe -r rt2500, but it couldn't find it.How do I find the device name? 

lsusb reports Ralink rt2570/RT<I forget the number>. 

I thought about doing the instructions from here [http://rt2x00.serialmonkey.com/wiki/index.php?title=Rt2x00_GIT_instructions](http://rt2x00.serialmonkey.com/wiki/index.php?title=Rt2x00_GIT_instructions). Then configuring it after.

My questions are: 

1. How do I find the device name of my wireless adapter so I can remove the module? 

2. Do I blacklist the device after?

3. Do I run ndiswrapper, with the current windows drivers, or use the linux sources?

Thanks!

---

