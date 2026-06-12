---
title: "Just finished installing drivers - sytem won't boot now"
date: 2011-11-13
forum: General Help
---

### Post by altjx on 2011-11-13
I just finished installing ATI video drivers from the site, and now this is what I'm getting upon reboot:

Sigh... Any idea? It won't go any further than this. I've tried rebooting it 3 times since the install. This screen comes up after the purple Ubuntu screen, and right before it gets to the login screen.

Picture attached.

---

### Post by Cyclane on 2011-11-13
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

To uninstall and return to open source drivers:
> $ sudo sh /usr/share/ati/fglrx-uninstall.sh
$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo rm -rf /etc/ati

If you wish to use fglrx drivers post the output of:
> lspci | grep VGA

---

### Post by altjx on 2011-11-13
> **Cyclane said:**
> [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

To uninstall and return to open source drivers:


If you wish to use fglrx drivers post the output of:

Thank you. I'm sitting at the full screen prompt still, and I just performed the sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core. (the 5th command in that quote), and I'm getting this in return

Reading state information - done
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded
need to get  kb of archives
after this operation, 0 b of additional disk space will be used
E: internal error, no file name for libgl1-mesa-dri.

Can I continue without worrying about that error?

EDIT: Thanks dude. I'm back at the login prompt! Should I try reinstalling that ATI driver from ATI's site? Maybe something went wrong?

---

### Post by Cyclane on 2011-11-13
that error is described in the link I gave you:

> If you receive
$ E: Internal Error, No file name for libgl1-mesa-dri
Change the third command above to:
$ sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:i386 libgl1-mesa-dri:amd64 xserver-xorg-core

So change the 'sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core' to the command above.

---

### Post by altjx on 2011-11-13
Thanks. Got it working. Do you think it's worth installing the ATI drivers from the site now? Or just use hte ones from the ADditional Drivers?

---

### Post by Cyclane on 2011-11-14
Could you post the output of: lspci | grep VGA

---

