---
title: "New video card Ububtu won't boot"
date: 2010-11-11
forum: General Help
---

### Post by Charles Vairin on 2010-11-11
Installed 10.4 lts on a Dell dimension 2350. Runs fine except that the video failed and a bar pattern is painted on the upper half of the screen. I works after a reboot for a while. So, I figured that the video card was failing and I replaced it with a ATI RAGE 128PRO 32 MB. Since the failed video is integrated into the mother board, the BIOS were modified to select the PCI bus. The initial Dell screen work and the initial UBUNTU screen with the four blinking dots come up but that is as far as the boot proceeds. The same result occurs when booting from the CD. Any suggestion would be appreciated.

Charlie

---

### Post by papibe on 2010-11-11
Did you do any custom settings for the old card? if you did, it may be possible that they are still stored on the X Windows config file. If you delete (or rename) it, you may start as a clean start (in terms of graphic cards and drivers).

To do this, boot on the recovery mode (text mode). Drop to a root shell and then do this:
```
# mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old 
```

Then reboot your system:
```
# reboot
```
and now go to the usual graphic mode.

Good Luck!

---

