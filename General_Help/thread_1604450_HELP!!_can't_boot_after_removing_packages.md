---
title: "HELP!! can't boot after removing packages"
date: 2010-10-24
forum: General Help
---

### Post by @dministrator on 2010-10-24
Hey all, as the title suggests I stupidly removed some packages after my iPhone 4 tethering stopped working. In an attempt to reinstall the tethering packages I did a search for 'iphone' in the software center and removed all found packages, I got to the last one and all I remember is something about python? Then bang... system froze and now it won't boot, gets to *checking battery state... and no further. It is a toshiba r600 laptop running maverick meerkat 10.10..

Any help greatly appreciated! Cheers.

---

### Post by MagnusWi on 2010-10-26
I have the same problem, after trying to fix the tethering issue with:

[I]# sudo apt-get uninstall gvfs ipheth-dkms ipheth-utils
# sudo apt-get install gvfs ipheth-dkms ipheth-utils

[/I]The problem described here happened to me aswell! I'm on a TravelMate 8371

---

### Post by tripmix on 2010-10-26
If you get to the checking battery part it seems to boot just fine, you just got a broken x. Try pushing alt+f1 then type "apt-get update" and "apt-get install xorg gdm gnome", it might help. Useful info can be found in /var/log/Xorg.0.log

---

### Post by stinkeye on 2010-10-26
This is what you remove if you uninstall gvfs.

---

### Post by @dministrator on 2010-10-28
> **tripmix said:**
> If you get to the checking battery part it seems to boot just fine, you just got a broken x. Try pushing alt+f1 then type "apt-get update" and "apt-get install xorg gdm gnome", it might help. Useful info can be found in /var/log/Xorg.0.log

Thanks! Ill give that a go tonight when I get home. Really need to get my machine back up and running without rebuilding the whole thing. I have like 3 virtual machines which I spent hours setting up!

---

### Post by @dministrator on 2010-10-30
For the record, It worked! Pressing ALT+F1 gave me a console to log into and check the apt logs to see which packages were removed.

I installed the removed packages, some were gnome-session, gdm and a couple of others.

---

