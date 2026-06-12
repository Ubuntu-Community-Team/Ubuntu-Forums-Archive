---
title: "Package dependencies ?"
date: 2010-07-02
forum: General Help
---

### Post by oygle on 2010-07-02
Running 9.04 and notice that both QT3 and QT4 seem to be installed. If I use 'System | Preferences' there is a 'QT4 Settings'.

Is there a method to go through all the apps, and see if QT3 is needed, as I'd rather get rid of it if it is not used/needed by any of the apps.

Oygle

---

### Post by warfacegod on 2010-07-02
The easiest way I know of is to find the package in Synaptic and mark it for removal. If something else is dependent on it, Synaptic will tell you that it also needs to be removed. So if nothing shows up then you *should* be fine.

---

### Post by oygle on 2010-07-02
Thanks, I searched for QT3 and there are a few packages, deleted one named qcad as I don't use it. When I now search for QT3 in Synaptic, there are only 3 installed packages. Would be nice to know if they are used, and by what.

There is a package called apt-rdepends, which recursively lists package dependencies. Also, I see that apt-cache can do a depends on a package or an rdepends. Some graph options there.

---

### Post by warfacegod on 2010-07-02
You can right click a package and select Properties. In that window, select the Dependencies tab and in the drop down menu select Dependent Packages.

---

