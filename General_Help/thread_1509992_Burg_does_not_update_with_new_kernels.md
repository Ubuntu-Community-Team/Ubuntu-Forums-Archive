---
title: "Burg does not update with new kernels"
date: 2010-06-15
forum: General Help
---

### Post by dcstar on 2010-06-15
The graphical alternative boot loader to Grub2, burg, still has a few bugs.

One is that when a new kernel is installed, you have to manually run update-burg unless you manually modify the /etc/kernel-img.conf file.

This is outlined at: [http://ubuntuforums.org/showthread.php?t=1412906](http://ubuntuforums.org/showthread.php?t=1412906)

I have just created a bug so the burg developer can fix this:

[https://bugs.launchpad.net/burg/+bug/594431](https://bugs.launchpad.net/burg/+bug/594431)

---

