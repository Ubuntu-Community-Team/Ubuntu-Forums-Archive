---
title: "Grub showing Debian planet image in background"
date: 2011-06-23
forum: General Help
---

### Post by 3vi1 on 2011-06-23
Okay, so I ran into some issues with my Oneiric testing today, so I reinstalled Natty clean.  I re-installed all my favorite packages and dev tools (about 800MB+ of them), rebooted....

And my was I quite surprised to be greeted by a Grub login screen that was showing the Debian name in the bottom right, with the planet at the bottom.  I'm quite familiar with this from my Debian VMs... but had never seen it on my main system before.

Does anyone have *any* idea which packages I could have installed/removed that caused Grub to revert to this behavior?  Has this happened to anyone else?

It works fine... it's just not at all expected as I've installed Natty at least 4 times in previous testing and never seen this behavior.

UPDATE:  This is not *really* solved, as I still have no idea why grub happened to show the debian background, but I dumped another image in the grub directory and ran the update to replace the background with my own.  So, I'm done wondering about it at this point.

---

### Post by mr_niceguy on 2011-09-07
I got this after installing ntfs-config

Removed it and boot went back to normal.

---

### Post by Joshas on 2011-11-23
Got the same issue (debian grub background) after installing xfce-desktop in Ubuntu 11.10.

SOLUTION: remove desktop-base package (sudo apt-get remove desktop-base).

---

### Post by ON-F on 2012-07-02
Thanks, I've solved the same problem also in 12.04 using your advice. :p

---

