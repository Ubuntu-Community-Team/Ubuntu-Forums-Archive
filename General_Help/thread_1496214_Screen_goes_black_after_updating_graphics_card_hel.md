---
title: "Screen goes black after updating graphics card: help?"
date: 2010-05-29
forum: General Help
---

### Post by losthighway on 2010-05-29
I installed Ubuntu 9.10 on my brand new Sony Vaio laptop. The installation went fine, but whenever I try to install the restricted driver to update my graphics card (whenever you click on Hardware and it says it's 'recommended' you update to accelerated graphics) so I can use Compiz, when it reboots after the install, the screen goes black and won't do anything. It shows the splash screen, but after that, the desktop never shows up and the screen goes black. I've tried it twice and had to completely reinstall Ubuntu from the CD every time because I can't see the desktop after it boots up. The sticker on my laptop says I have Nvidia Geforce with Cuda...whatever that is. And it's a brand new laptop. Anyone know why I can't update my graphics?

---

### Post by Lampi on 2010-05-29
Try to get /var/log/Xorg.0.log and look for (EE) (WW) entries

You might need to boot from livecd and mount your ubuntu installation there.

While you're at it I recommend some changes in grub2, so you can bring up the grub2 menu for a few seconds with the failsafe boot entry:

edit /etc/default/grub and modify these lines as root:

```
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT="3"
```

now run 'update-grub' to update the menu

Like this you will see the grub menu for 3 seconds at bootup, and you can select the failsafe mode.

---

