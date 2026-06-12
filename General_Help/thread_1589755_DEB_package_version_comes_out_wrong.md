---
title: "DEB package version comes out wrong"
date: 2010-10-06
forum: General Help
---

### Post by RageLtMan on 2010-10-06
While trying to get a new revision of ntfs-3g packaged for my OS (2010.10.02) i've run into an odd issue. I pulled the ntfs-3g sources, and got the package sources for the ntfs3g debs (apt-get source ntfs3g).

I pulled the <src dir>/debian directory into the new sources, went into <new src dir>/debian/<package names>/DEBIAN and altered the versions in the control files to reflect the current version. However, during dpkg-build, the versions revert to the original package version which is 2010.03.06. When these debs get installed, apt-get update thinks that despite both the version of the installed package, and the version of the upstream package being the same, that it should replace the one i made with the upstream. 

What do i need to change in the <src>/debian/... config/control files to make the new version number stick?

---

### Post by mc4man on 2010-10-06
Haven't had a look at that source (ubuntu) but at a min either edit the last  changelog entry or make a new one. (the one in /debian
(if there are any .install files take a look there also.

---

### Post by RageLtMan on 2010-10-06
interesting, changelog did indeed contain old version as top entry. Are the debian build mechanisms smart enough to parse that in order to grab current version so as not to have to edit the control files for each package being built? I never cease to be impressed by the ingenuity of open source devs, re-building, lets see what happens.

EDIT: brilliant, thank you, that worked :)

---

