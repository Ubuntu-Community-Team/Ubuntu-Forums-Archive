---
title: "change /home/user location"
date: 2010-06-28
forum: General Help
---

### Post by Mister_r on 2010-06-28
I have just started using ubuntu.
I have one PC with dual boot, ubuntu and Windows7.
I wonder if it is possible in ubuntu to modify the localization of the /home/user folder? This folder has other folders (documents, music, etc). I want to point this folder to an external drive that I have mounted in /dados.
Is this possible? How can I do it?

---

### Post by colorlessprism on 2010-06-28
symlinks is what i would use:
[http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html](http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html)

---

### Post by philinux on 2010-06-28
> **Mister_r said:**
> I have just started using ubuntu.
I have one PC with dual boot, ubuntu and Windows7.
I wonder if it is possible in ubuntu to modify the localization of the /home/user folder? This folder has other folders (documents, music, etc). I want to point this folder to an external drive that I have mounted in /dados.
Is this possible? How can I do it?

You could open /dados with nautilus then right click on a folder there and choose Make Link. Then drag and drop or cut and paste that Shortcut into your user folder.

---

