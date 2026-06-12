---
title: "Recompiled package and Update Manager in Karmic"
date: 2010-04-12
forum: General Help
---

### Post by unknown3 on 2010-04-12
Thank to a great thread:

[http://ubuntuforums.org/showthread.php?t=101097](http://ubuntuforums.org/showthread.php?t=101097)

I recompile pulseaudio packages in Karmic x64 (trying to boost performance).
The packages compile and installed successfully.

However, the "Update Manager" always prompted me to update the package (the version string is the same)

screenshot attached, is it a bug? or i forget some setting?

---

### Post by philinux on 2010-04-12
In synaptic highlight the package then choose.

Package>Lock Version.

You can undo this any time.

---

### Post by unknown3 on 2010-04-12
thx for your help. but if i lock the version, will update manager notify me when there is a newer version?

also why update manager prompt me to update a package with same version string?:confused:

---

### Post by unknown3 on 2010-04-15
i google for a while and still no solution

at last, i use a "dirty" trick

before build the package, do to the source folder, in the debian/changelog file, append "a" to the version string.

so that the version like

1.0 -> 1.0a

---

