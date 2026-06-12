---
title: "update manager"
date: 2009-10-29
forum: General Help
---

### Post by bds28338 on 2009-10-29
does update manager actually update programs to new versions?
or does it just install security updates, etc etc?

add/remove manager has a column which states "canonical-maintained programs" I try to always get programs from there because I believed update manager would always provide me with the newest version and I would only have to manually update programs I did not get from there. Is this true? or was I under false assumptions?

---

### Post by zvacet on 2009-10-29
You can get new versions of packages with update manager but that is in just few situations.Ubuntu doesn't add new versions of software if it is not stable,so it is rare situation to get new versions with update manager.Yes,you will get security updates witch is,in my opinion,more important then new version of some package.For package installation use add/remove and synaptic.

---

### Post by Gaweph on 2009-10-29
Im pretty sure that the Update manager will update packages.

For example say your using program X.V2 and a new stable release of X.V3 is available in the repositories, then the update manager will update the package for you.

This is the whole point of using a package based system, it lets you update and manage everything from a single location.  The repository checks for newer versions of installed packages, this will include only the stable releases by default.

Although you are able to add other repos which can contain more cutting edge (unstable) versions of packages.

Gaw

---

### Post by donato roque on 2009-10-29
From the security view, using apt-Synaptic/Update Manager ensures that what you download is safe software.  To keep it safe and up to date, canonical maintains the version for that particular ubuntu release (jaunty, karmic).  These version of the software has the stamp of approval from the security team at Ubuntu. Once they upload new version of the software, you are notified by Update manager.

This does not stop other third parties from releasing a "new" version of the software apart from Canonical's.  You will read of PPA's and Third Party Repositories in the forum.  You may elect to enable these in the Software Sources to get their version of the software.  

I'd say check the forum first before downloading any software outside the main repositories.

---

