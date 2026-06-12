---
title: "How to edit Grub menu in Lucid?"
date: 2010-07-25
forum: General Help
---

### Post by Flexico on 2010-07-25
In Intrepid, I was able to totally customize my Grub listing, but now that I have Lucid, the files are all different and I've been all over the net looking for how to edit them and it's just confusing!

---

### Post by collinp on 2010-07-25
There's an Ubuntu Community Help page dedicated to Grub2. Although it is pretty technical in places, you should be able to find what you are looking for easily enough: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by oldfred on 2010-07-25
You still can do a custom menu.

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

I believe drs305 updated to allow various numbers of  lines to show but I have not tried that yet.

---

