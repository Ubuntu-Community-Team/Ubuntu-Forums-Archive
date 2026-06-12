---
title: "Kpackagekit wants to remove kubuntu desktop?"
date: 2011-05-06
forum: General Help
---

### Post by hg21 on 2011-05-06
I just tried to remove samba from a new upgrade to 11.04 via Kpackagekit it said "additional packages to remove kdesktop".  This seems weird?

---

### Post by matthewbpt on 2011-05-06
kubuntu-desktop is just a metapackage which pulls in all kubuntu related stuff if installed, it is perfectly safe to remove it. The reason it wants to remove it is because samba is a package pulled in by it. Removing it shouldn't remove any other important Kubuntu packages. The only time I would recommend reinstalling it is when upgrading to a new release of Kubuntu, such as 11.10 in October. Here is a slightly more technical explanation of metapackages [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages) .

EDIT: Why do you want to remove samba anyway?

---

### Post by hg21 on 2011-05-07
> **matthewbpt said:**
> kubuntu-desktop is just a metapackage which pulls in all kubuntu related stuff if installed, it is perfectly safe to remove it. The reason it wants to remove it is because samba is a package pulled in by it. Removing it shouldn't remove any other important Kubuntu packages. The only time I would recommend reinstalling it is when upgrading to a new release of Kubuntu, such as 11.10 in October. Here is a slightly more technical explanation of metapackages [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages) .



EDIT: Why do you want to remove samba anyway?

Thanks for explanation

Don't need samba

---

