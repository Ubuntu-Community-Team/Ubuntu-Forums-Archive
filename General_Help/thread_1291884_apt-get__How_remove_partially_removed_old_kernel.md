---
title: "apt-get : How remove partially removed old kernel ?"
date: 2009-10-15
forum: General Help
---

### Post by hg21 on 2009-10-15
When I preview this I found it was tagged SOLVED this is not so, I thought I'd tagged it General

I frequently get a problem with software updates which I think is caused by a badly/incompletely removed very old kernel. 

The relevant apt-get message is:- 

Removing linux-ubuntu-modules-2.6.24-21-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-21-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
Cannot find /lib/modules/2.6.24-21-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-21-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-21-generic (--remove):
 subprocess post-removal script returned error exit status 1

A search with locate does not find 2.6.24-21 anywhere so, I assume, it is listed in a dpkg file somewhere but I can't find it.

---

