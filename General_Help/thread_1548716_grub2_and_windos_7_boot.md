---
title: "grub2 and windos 7 boot"
date: 2010-08-08
forum: General Help
---

### Post by xnihsnek on 2010-08-08
hi, i just bought a dell studio 15 with windows 7. a made a partition and installed ubuntu 10.04 LTS. when i restart or shut down my computer from windows 7 and start it again i got a message that there is no "module name found" so i need boot from the liveCD and reinstall de grub so i can enter either windows or ubuntu. is there a way to solve this

---

### Post by Darkness Des on 2010-08-08
You probably have Dell Datasafe installed. If you don't use it, uninstall it. If it detects GRUB (or anything not Windows related) in the MBR then it will corrupt it. If you do use it, use the Alternate Install CD to put GRUB on your Ubuntu partition, then download the latest EasyBCD Build from here (account needed) and use it to set up an Ubuntu entry in the Windows 7 bootloader.

[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

10.04 uses GRUB2, and EasyBCD Autodetects this.

---

### Post by Rubi1200 on 2010-08-08
You need to boot the computer with the Ubuntu CD and choose to try in live mode not install.

Then, click on the link at the bottom of my post and follow the instructions there.

Post the results back here before taking any further steps.

Thanks.

---

