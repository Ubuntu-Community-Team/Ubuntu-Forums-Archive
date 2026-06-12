---
title: "How to update a package manually?"
date: 2006-02-23
forum: General Help
---

### Post by Morbett on 2006-02-23
I'm trying to update libc6 2.3.2 (stable) to libc6 2.3.5 (testing).  Since the latter is not availably through synaptic, I downloaded the .deb file for it.  Now I need to replace the 2.3.2 with 2.3.5, without having to uninstall 2.3.2.  (If I uninstall 2.3.2 first, I'd have to uninstall tons of important packages).

Is there a way to manually update it with the new .deb file using Terminal?

---

### Post by Morbett on 2006-02-23
Bump.  I've done a few google searches but still no luck...

Thanks for you help.

---

### Post by knalle on 2006-02-23
download the deb file and do "sudo dpkg -i somepack.db"

---

### Post by Morbett on 2006-02-23
Thanks.  I do know about that command, but I get this:

dpkg: regarding libc6_2.3.5-13_i386.deb containing libc6:
 libc6 conflicts with initrd-tools (<< 0.1.79)
  initrd-tools (version 0.1.77ubuntu3) is installed.
dpkg: error processing libc6_2.3.5-13_i386.deb (--install):
 conflicting packages - not installing libc6
Errors were encountered while processing:
 libc6_2.3.5-13_i386.deb


Does this mean I have to upgrade initrd-tools or something?

---

### Post by Trab on 2006-02-23
yes, it means u need to upgrade that...
have you tried looking in synaptic and checking to force version to testing?
it would be easier that way...
latz
-Trab

---

### Post by Morbett on 2006-02-23
Thanks so much for your help.

I checked on forcing the version to testing, but the testing one isn't available.   libc6 doesn't seem to go past 2.3.2 in Synaptic.

I guess I'm stuck in what they call dependency hell.  I can't install libc6 2.3.5 because it conflicts with initrd-tools...

---

### Post by Morbett on 2006-02-23
I've been trying to get all these dependencies just to install gstreamer0.8-faad in order to use .aac.

I've hit a brick wall for some reason.  Do I need to upgrade from Hoary to Breezy or something?!

---

