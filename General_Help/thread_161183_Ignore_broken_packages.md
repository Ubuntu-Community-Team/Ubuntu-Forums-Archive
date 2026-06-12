---
title: "Ignore broken packages"
date: 2006-04-16
forum: General Help
---

### Post by madplanet on 2006-04-16
I know this has been asked before, I've searched for an answer, but is there a simple way to get synaptic to ignore a broken package, so that I can still get security updates?

My only solution right now is to do
   sudo apt-get install -f
then do an update and then reinstall the broken package. But this is a manual process (and I'm lazy!)

Out of interest, the package is BibbleLite, which has an xlibs dependency, however, dapper no longer uses xlibs - hence a forced install (and a broken, but working, package)

Many thanks
mP

---

### Post by kevinlyfellow on 2006-05-31
I could really use this too, since I made gjay use beep-media-player instead of xmms.  What really annoys me is the update notifier telling me that I have a broken package, and therefore not immediatly knowing if I have updates or not.

---

### Post by az on 2006-05-31
You will have to backport the package and change the dependencies in the control file.  So, find the package's source and rebuild it.


A broken package is a broken package.  It may run fine now, but if somehting updates to a different version, it may stop working.  That's why the package manager will not let it go.

---

