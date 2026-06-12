---
title: "Remove samba-common, will also remove ubuntu-desktop?"
date: 2009-11-13
forum: General Help
---

### Post by cpthk on 2009-11-13
I have ubuntu 9.10. I try to uninstall samba-common, it prompts me that several packages will also be removed. I see one is ubuntu-desktop. I was wondering what does it has to do with desktop?

Thanks.

---

### Post by Anarci on 2009-11-13
ubuntu-desktop is a meta package, a package which in itself does not install anything but has dependencies. This is used to *group* packages, other meta packages are kubuntu-desktop, ubuntu-minimal etc. Uninstalling a meta package will not remove any software from your system. Although you can remove them - as the dependant packages are not removed as well - it is not recommended as this can affect updates.

You can read more here: [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

