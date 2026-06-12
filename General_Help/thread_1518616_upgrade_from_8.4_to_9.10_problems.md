---
title: "upgrade from 8.4 to 9.10 problems"
date: 2010-06-26
forum: General Help
---

### Post by Andres Gonzalez on 2010-06-26
I just upgraded to 9.10 and now my software builds do not compile.

pkg-config --cflags gtk+-2.0

no longer works because it can no longer find the gtk+-2.0 package.

Did this change between versions?   Why did upgrading to a newer version uninstall the older libraries?  I cannot even find ANY newer version!!  gtk+-2.1 ??    2.2 perhaps??

Why didn't the upgrade at least inform me that I would have to upgrade all of my software development makefiles?

What gtk+ version was installed in ubuntu 9.10 and where is it located?

Thanks,

-Andres

---

### Post by gzarkadas on 2010-06-26
From what I see the version in 9.10 is 2.0. You may have to install the `libgtk2.0-dev' package to get the functionality you want; I don't think it is installed by default.

Open the Synaptic Package Manager and enter `libgtk2.0' on the Quick Search Box; it will show all related packages.

---

