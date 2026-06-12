---
title: "Video issue with Dual boot windows 7 and ubuntu"
date: 2012-03-05
forum: General Help
---

### Post by vanzylnb on 2012-03-05
I have installed windows 7 and ubuntu on same pc. When booting in ubuntu my screen goes blurry and dual cursor. I do make out the log in screen and type in pw. the the screen goes blank and orange again with dual cursor and nothing else.
MSI mb with ATI Radeon 7760 GFX card.

---

### Post by oldfred on 2012-03-05
Moved to your own thread.

You should try nomodeset, or  radeon.modeset=0 or xforcevesa

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

