---
title: "Blacklist packages?"
date: 2010-09-30
forum: General Help
---

### Post by mutantstargoat on 2010-09-30
I've just installed Ubuntu 10.10 and fired up Synaptic.  Go to the Sections tab and select the KDE sections.  Lock version on all packages.  Go to Gnome sections select a lot of things for complete removal.  Check the Marked Changes tab.  At the bottom quite a few KDE packages are marked for installation.  I had assumed that locking the uninstalled KDE packages would prevent them from installing.  This is not the case.  Is there some way I can prevent Synaptic, or any other package manager, from ever installing anything related to KDE and Qt?

---

### Post by ajgreeny on 2010-09-30
I'm not at all sure that you can lock (or pin) the versions of packages that you don't have installed, as there will be no candidate version already present to pin.  If a KDE or qt package is being offered in updates, you must have something that requires them as dependencies, and you may also have the preferences in synaptic set to include recommended packages as dependencies, which I think is the default.

Try deselecting this option in synaptic preferences, and see if it stops those KDE apps from appearing in the updates etc etc.

---

