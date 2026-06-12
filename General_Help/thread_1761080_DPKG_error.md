---
title: "DPKG error"
date: 2011-05-17
forum: General Help
---

### Post by snorkytheweasel on 2011-05-17
I'm trying to upgrade virtualbox 3.2.xx to 4.04.

The ubu repositories don't have the current version, so I downloaded the 4.04 .deb from virtualbox.org

This command:
```
sudo dpkg --install /home/myfolder/Downloads/virtualbox-4.0_4.0.8-71778~Ubuntu~maverick_i386.deb
```

Throws this error:
```
 virtualbox-4.0 conflicts with virtualbox
  virtualbox-3.2 provides virtualbox and is present and installed.
dpkg: error processing /home/myfolder/Downloads/virtualbox-4.0_4.0.8-71778~Ubuntu~maverick_i386.deb (--install):
 conflicting packages - not installing virtualbox-4.0
Errors were encountered while processing:
 /home/myfolder/Downloads/virtualbox-4.0_4.0.8-71778~Ubuntu~maverick_i386.deb
```

How do I get this to install?

---

### Post by TeoBigusGeekus on 2011-05-17
Perhaps you should first remove the older version?
Also, have you checked the dependencies for the new one?

---

