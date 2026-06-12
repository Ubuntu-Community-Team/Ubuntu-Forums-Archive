---
title: "Update gcc and gfortran"
date: 2011-12-03
forum: General Help
---

### Post by archie569 on 2011-12-03
Hi: 
I have installed ubuntu 10.04 version with gcc and gfortran 4.4.3.
Is there any advantages to install the newer versions (4.5, and 4.6)? If it is, the only way to install it is by downloading the package manually?

---

### Post by hwttdz on 2011-12-03
The possible advantages would be reduced compile time, reduced runtime or bug fixes.  The compile time and runtime differences are likely to be negligable.  I've only ever experienced one gfortran bug, and I think it was in a more recent version anyways.  So there's certainly no overwhelming reason to upgrade.  On the other hand, all of these are good things, so if there's not a reason against you might as well.

The possible reasons aganst are 1) incompatibility - occasionally flags change, which can be a pain for makefiles, 2) the annoyance of upgrading, which really depends on the system.

You can download the debs and go that way, but I've always found compiler installs to be annoying, so I'd probably just stick it out until you upgrade your system.

---

