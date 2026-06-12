---
title: "Cannot reinstall Unity, Ubuntu-desktop, GIMP"
date: 2012-03-07
forum: General Help
---

### Post by rtimai on 2012-03-07
Recently Update Manager kept showing a libgimp2.0 update failing. Apt-get indicated that it depended on a libglib2.0 update which was not available. I UNWISELY downloaded the libglib2.30.2 package from the GIMP development site, and force installed it. But then the failed libgimp2.0 update disappeared from Update Manager.

So then I manually force-removed the installed libgimp2.0 in order to update it to the new version. (One idiotic act leads to another.) This PURGED Unity, Ubuntu-desktop, weather-indicator, and GIMP as well as libgimp2.0.

Now I cannot reinstall Unity or Ubuntu-desktop or GIMP or libgimp2.0. Each attempt complains of broken packages. Attempting to fix broken packages complain that a requested package is not available, or are unresolvable because "you have held broken packages."

I attempted to backtrack, and force remove the offending libglib2.0 update, but dpkg complains that the package name contains the illegal '~' (tilde) character. Renaming the package doesn't work -- dpkg then claims no installed package with the (renamed) name is found. It's one catch-22 after another.

I'm running LXDE right now with no major functional loss, except for the major problem that I can't reinstall GIMP.

Short of backing up my Documents folder (18GB,) and performing a complete re-install, is there a way to restore Oneiric to the state before I started down this foolish path? Thanks for reading.

Ubuntu 11.10 (upgraded)
AMD Turion II P520 Dual-Core
(HP dv6 3012he notebook)

---

### Post by rtimai on 2012-03-14
Just wanted to report that I solved the "held packages" problems blocking re-installation of the Ubuntu-desktop modules, GIMP, weather-indicator and libgimp2. I re-installed Oneiric amd64. The great news is that Ubuntu now provides for a non-destructive re-installation by selecting "upgrade 11.10 to 11.10." Only a few minor applications were removed (easily re-installed,) and all of the significant Unity desktop, system, and application preferences were preserved. I backed up all of my Documents folder, but found that I didn't need to, as they were not touched. Ubuntu installation keeps on improving with every release. 

LESSON LEARNED: Never force an update that has failed in Update Manager.

---

