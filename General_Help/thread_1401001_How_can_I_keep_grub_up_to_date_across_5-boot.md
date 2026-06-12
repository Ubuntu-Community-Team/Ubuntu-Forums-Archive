---
title: "How can I keep grub up to date across 5-boot?"
date: 2010-02-07
forum: General Help
---

### Post by magicman5421 on 2010-02-07
On my computer, I boot 5 different operating systems (Windows, ubuntu studio, and 3 versions of Ubuntu), but my grub install is grub 2 on ubuntu 9.10. If I do a kernel upgrade on any of the other ubuntu operating systems, how do I update my grub configuration on ubuntu 9.10 so I can boot it?

---

### Post by oldfred on 2010-02-07
With grub2 a sudo update-grub will find the new kernels and add them to your grub.cfg. But with so many operating systems you will get a large menu. I liked chainbooting as that required no updating of the first boot and the second grub menu was automatically updated.

See this about config file for grub2.
Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)

You do not have to refer to the latest kernel but to a standard link that will take you to that.

---

